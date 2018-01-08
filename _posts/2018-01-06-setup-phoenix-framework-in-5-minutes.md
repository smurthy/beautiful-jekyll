---
layout: post
published: true
title: Set up Phoenix on Webfaction
---
## Welcome the erlang web stack: Phoenix and Elixir

I was looking for a web framework with high fault tolerance, distribution, concurrency, and availability in my projects. For whatever reason I was pursuing node.js and expressjs to achieve this task. Its anychronous processing on a single thread was definitely not optimal for my use case. 

This lead me to Erlang. Erlang was born in telecom by Ericsson in the 80s. It reportedly handles around 50% of the world telecom traffic. You also can look at the word's other meaning, [a unit of telecommunications traffic measurement](http://www.erlang.com/whatis.html#erlang), to understand its origin and importance.

My first experiment was to just setup a web framework something like Ruby on Rails but using the erlang web stack (Erlang VM, Phoenix Framework, and Elixir language) to benefit from points mentioned above. I stumbled upon Elixir/Phoenix after reading Hilmarrson's [post](https://14islands.com/blog/2016/08/16/phoenix-framework/) outlining just the reasons I needed to try this guy out.

Webfaction didn't give me access to install via yum package manager, so everything was compiled from source. 

## The quick and dirty guide

**Install Erlang**
```
 wget http://www.erlang.org/download/otp_src_20.2.tar.gz
 tar -xf otp_src_20.2.tar.gz
 cd otp_src_20.2
 ./configure --prefix=$HOME
 make
 make install
 export PATH=$PATH:/home/[username]/otp_src_20.2/bin
```
**Install Elixir**
```
 git clone https://github.com/elixir-lang/elixir.git
 cd elixir
 make 
 export PATH=$PATH:/home/smurthy/elixir/bin
```
**Install Phoenix**
```
 mix local.hex
 mix archive.install https://github.com/phoenixframework/archives/raw/master/phx_new.ez
```

**Install inotify tools** 
```
 wget http://github.com/downloads/rvoicilas/inotify-tools/inotify-tools-3.14.tar.gz
 tar -xf inotify-tools-3.14.tar.gz
 cd inotify-tools-3.14
 ./configure 
 make 
 make install
```

{: .box-warning}
**Warning:** Compilation failed on webfaction if you care for live reloading. Optional.

**Scaffold a default project** with mysql database and no [brunch](http://brunch.io/)

```
 mix phx.new helloworld --database mysql --no-brunch 
```
![phoenixscaffold.png]({{site.baseurl}}/img/phoenixscaffold.png)

Setup database config at config/dev.exs (I'm using development). This can be skipped with the `--no-ecto` parameter when scaffolding. If you chose the default database (postgres ) you can [switch it back to mysql](https://phoenixframework.readme.io/docs/using-mysql).

{: .box-warning}
**Warning:** Brunch install failed on webfaction due to unsupported linux architecture. Optional.

![bruncherror.png]({{site.baseurl}}/img/bruncherror.png)

Finally, start up the server and watch the server output.
```
 mix phx.server
```
![phoenixlog.png]({{site.baseurl}}/img/phoenixlog.png)


Ta-da. The default page on your site.

![defaultpage.png]({{site.baseurl}}/img/defaultpage.png)
