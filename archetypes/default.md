+++
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
date = '{{ .Date }}'
lastmod = '{{ .Date }}'
slug = "{{ time.Now | time.Format "2006-01-02T15-04-05" }}"
summary="Summary of your new article."
categories = ['Tech']
tags = ['maths' ]
+++

And this is where you write your new article

## Subtitle 

The next section

### Sub sub title


#### Sub sub sub title
