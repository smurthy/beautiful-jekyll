---
layout: post
published: false
title: Setting up Phoenix Framework on Webfaction
---
## Welcoming the erlang web stack: Phoenix and Elixir

I often get asked on which programming language or framework is my expertise. A better question would be what problems am I trying to solve and why was the language/framework used the best choice? There's no one size fits all and my expertise changes based on the problem I'm solving at the moment. Previous experience taught me, though, that using right tool outweighs any reluctance to learn new languages based on personal bias. I've seen programmers refuse to try new stacks because of personal bias against that langauge used. If you hate javascript you'll never willingly use node.js even if your use case is squarely in node.js's wheelhouse.

I used Java and JBoss, for instance, in my stint at [Micros](https://www.oracle.com/corporate/acquisitions/micros/index.html) because it was optimal, at the time, in handling high transaction [ETL](https://www.webopedia.com/TERM/E/ETL.html) workloads. I used Ruby on Rails in the early days since I got shit done, fast, for small scale web apps without the need for an army of additional developers. The rails actual performance didn't matter for a small user base. I opted for speed of development.

Furthermore, you wouldn't think a language like Fortran is servicable today but it's still the most efficient language for complex mathematical calculations. [Why?](https://scicomp.stackexchange.com/questions/203/what-makes-fortran-fast). Intel even built specific libraries for this langauge. You need only peek into any research lab to find out this out. Why bother trying to force this into another language, say Java, when there are domain-specific optimizations built over _DECADES_ into Fortran? You wouldn't.  

**Use tool that fits your case even if it's not the marketable skill to have. Trends change.**

These days I crave fault tolerance, distribution, concurrency, and high availability in my projects. For whatever reason I was pursuing the trend, node.js, to achieve this task. It's anychronous processing on a single thread was definitely not optimal for my use case. 

This lead me to Erlang. Erlang was born in telecom by Ericsson in the 80s. It reportedly handles around 50% of the world telecom traffic. You also can look at the word's other meaning, [a unit of telecommunications traffic measurement](http://www.erlang.com/whatis.html#erlang), to understand its origin and importance.

My first experiment was to just setup a web framework something like Ruby on Rails but using the erlang web stack (Erlang VM, Phoenix Framework, and Elixir language) to benefit from points mentioned above. I stumbled upon Elixir/Phoenix after reading Hilmarrson's [post](https://14islands.com/blog/2016/08/16/phoenix-framework/) outlining just the reasons I needed to try this guy out.



Webfaction intro

![phoenixscaffold.png]({{site.baseurl}}/img/phoenixscaffold.png)
![bruncherror.png]({{site.baseurl}}/img/bruncherror.png)
![phoenixlog.png]({{site.baseurl}}/img/phoenixlog.png)
![defaultpage.png]({{site.baseurl}}/img/defaultpage.png)
