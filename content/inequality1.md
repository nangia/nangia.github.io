+++
date = 2025-08-17T15:09:17+05:30
lastmod = "2025-08-17T15:09:17+05:30"
title = 'An Inequality to Prove'
slug = 'kircak1.15'
summary='Find 3 digit natural numbers that are divisible by 2 or 3 but not by 7.'
categories = ['maths']
tags = ['Kircak' ]
[params]
  math = true
+++

## Problem

Prove that if \(p, q \gt 0\) and \(p + q = 1\), then

\[ (p + \frac{1}{p})^2 + (q + \frac{1}{q})^2 \geq 25/2\]

## Proof

Since \(p, q \gt 0\) therefore \(p + \frac{1}{p} \gt 0 \) and \(q + \frac{1}{q} \gt 0 \). As \(QM \geq AM\) for positive numbers:

\[ \sqrt{\frac{(p + \frac{1}{p})^2 + (q + \frac{1}{q})^2}{2}} \geq \frac{(p + \frac{1}{p}) + (q + \frac{1}{q})}{2}\]

Squaring both sides and rearranging:

\[\implies \frac{(p + \frac{1}{p})^2 + (q + \frac{1}{q})^2}{2} \geq [\frac{(p + q) + (\frac{1}{p} + \frac{1}{q})}{2}]^2\]

\[\implies (p + \frac{1}{p})^2 + (q + \frac{1}{q})^2 \geq \frac{1}{2}[(p + q) + (\frac{1}{p} + \frac{1}{q})]^2\]

\[\implies (p + \frac{1}{q})^2 + (q + \frac{1}{q})^2 \geq \frac{1}{2}[1 + (\frac{1}{p} + \frac{1}{q})]^2 \tag{1} \]

Since \(AM \geq HM\), we have:

\[ \frac{p+q}{2} \geq \frac{2}{\frac{1}{p} + \frac{1}{q}} \]

Using the fact that \(p + q = 1\) and rearranging:

\[ \frac{1}{p} + \frac{1}{q} \geq 4 \]

\[ \implies 1+ (\frac{1}{p} + \frac{1}{q}) \geq 5 \]

\[ \implies [1+ (\frac{1}{p} + \frac{1}{q})]^2 \geq 25 \]

\[ \implies \frac{1}{2}[1+ (\frac{1}{p} + \frac{1}{q})]^2 \geq \frac{25}{2} \tag{2} \]

From inequalities \((1)\) and \((2):\)

\[ (p + \frac{1}{p})^2 + (q + \frac{1}{q})^2 \geq 25/2 \]

Hence, proved.

## Reference

Problem 1.15 of [Inequalities by Ozgur Kircak](https://ozgurmath.wordpress.com/wp-content/uploads/2013/06/inequalities-book.pdf)
