---
layout: post
title: "The day WTF crashed our servers"
author: "Thomas Alex Mathew"
---

Today was an interesting day at work. Sometime in the morning, we got an alert saying one of our front-end servers went offline. On checking the server logs, we found that a student's answer had led to this crash. And the answer that took our server offline is (drum rolllll.....) :

{% highlight ruby %}
WTF!!!!!
{% endhighlight %}

Yup. Literally "WTF!!!!" is what took our server offline. That did make us say "WTF!!!" too. Quite a distant and faint echo.

The company I work for is all about online K-12 school assessments. A student happened to be responding to a **math question** where the student is expected to type out a simple math expression that's evaluated by our system, and then compared to the answer key. The expected answer was something in the line `3 x (45 / 9)`, which would be evaluated by our system to `15`. Now, this student got very frustrated with all the morning-math(yes, it's a new term I just keyed) they had to do and decided to type "WTF!!!!". Our evaluation engine, mistakenly, tried to evaluate `WTF!!!!` as a factorial. That led our poor server to compute a ridiculously impossible and massive number which resulted in a high CPU usage for a prolonged period. This was read as "offline" status by our alarm-systems.

Good news is the fix was easy. We just had to put in a check in all math-type questions that validate if the response is a math expression. Only if it's a valid math expression, we would evaluate it. But, really. WTF!!!
