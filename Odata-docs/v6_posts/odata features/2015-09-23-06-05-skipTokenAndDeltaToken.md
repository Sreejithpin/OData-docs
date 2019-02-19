---
title: "$skiptoken & $deltatoken"
description: ""
category: "6. OData Features"
author: Khairunj
ms.author: Khairunj
ms.date: 02/19/2019
ms.topic: article
ms.service: multiple
---

From ODataLib 6.12.0, it supports to parse $skiptoken & $deltatoken in query options.

## $skiptoken

Let's have an example:

{% highlight csharp %}
~/Customers?$skiptoken=abc
{% endhighlight %}

We can do as follows to parse:

{% highlight csharp %}
var uriParser = new ODataUriParser(...);
string token = parser.ParseSkipToken();
Assert.Equal("abc", token);
{% endhighlight %}

## $deltatoken

Let's have an example:

{% highlight csharp %}
~/Customers?$deltaToken=def
{% endhighlight %}

We can do as follows to parse:

{% highlight csharp %}
var uriParser = new ODataUriParser(...);
string token = parser.ParseDeltaToken();
Assert.Equal("def", token);
{% endhighlight %}