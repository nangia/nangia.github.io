---
title: "First Fibonacci Number with not Less than 1000 Digits"
date: "2013-09-15T00:05:00+05:30"
lastmod: "2014-09-20T21:26:00+05:30"
slug: fibonacci-num-with-not-less-than-1000digits
summary: "A Clojure program that calculates the first Fibonacci number with not less than 1000 digits is demonstrated."
categories:
- Programming
tags:
- clojure
---


Problem
-------
The Fibonacci sequence is defined as follows:  

- The first Fibonacci number is 1.
-  The second Fibonacci number is 1.
- After this any Fibonacci number is the sum of the preceding two Fibonacci numbers.

Thus, the first 10 numbers of the Fibonacci sequence are 1, 1, 2, 3, 5, 8, 13, 21, 34, 55. 

Find the first Fibonacci sequence with not less than 1000 digits.

This problem is slightly altered version of [Project Euler Problem 25](http://projecteuler.net/problem=25).

Solution in Clojure
------------------
{{< highlight clojure >}}
(defn fib-next [[fib1 fib2 number]]
  [fib2 (+ fib1 fib2) (inc number)])

(def fib-seq (iterate fib-next [1N 1N 1N]))

(defn lengthlessthan? [[fib1 fib2 number]]
  (< (.length (str fib1)) 1000))

((->> fib-seq
      (drop-while lengthlessthan?)
      (take 1)
      (first))
  2)
{{< /highlight >}}

Description
-----------
To solve this, first we define a function *fib-next* which takes in a vector with three numbers: nth Fibonacci number, (n+1)the Fibonacci number and n. Given this number it calculates a new vector with (n+1) Fibonacci number, (n+2) Fibonacci number and (n+1). Using this function we define an infinite sequence *fib-seq* to calculate this vector using the initialization vector [1N 1N 1N]. Since, we are likely to be dealing with large numbers, hence with prefix N after 1.

We define a function *lengthlessthan?* which returns true if the number of digits in a number are less than 1000 given a vector of the form generated by *fib-seq*. All that is being done is to convert the number into a string and then computing its length using *java.String.length()*.

With these definitions out of the way, we just generate this infinite sequence *fib-seq* and drop all vectors such that the number of digits in Fibonacci number is less than 1000. We take the sequence to include just the first such number with length not less than 1000, separate it out using first and then find the 3rd number in this vector.