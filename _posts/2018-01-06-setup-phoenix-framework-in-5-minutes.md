---
layout: post
published: false
title: Setting up Phoenix Framework on Webfaction
---
## Welcoming the erlang web stack: Phoenix and Elixir

These days I crave fault tolerance, distribution, concurrency, and high availability in my projects. For whatever reason I was pursuing the node.js to achieve this task. Its anychronous processing on a single thread was definitely not optimal for my use case. 

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

**Install inotify tools** (this failed to install on webfaction but it's optional)
```
wget http://github.com/downloads/rvoicilas/inotify-tools/inotify-tools-3.14.tar.gz
tar -xf inotify-tools-3.14.tar.gz
cd inotify-tools-3.14
./configure 
make 
make install
```

**Scaffold a default project** 
Brunch doesn't work on webfaction because of unsupported linux architecture.
```
mix phx.new helloworld --database mysql --no-brunch 
```

Setup database config at config/dev.exs (I'm using development). This can be skipped with -no_ecto when scaffolding.

If you chose the default database (postgres ) you can switch it back to mysql following these instructions: https://phoenixframework.readme.io/docs/using-mysql

Finally, start up the server:
```
mix phx.server
```



![phoenixscaffold.png]({{site.baseurl}}/img/phoenixscaffold.png)
![bruncherror.png]({{site.baseurl}}/img/bruncherror.png)
![phoenixlog.png]({{site.baseurl}}/img/phoenixlog.png)
![defaultpage.png]({{site.baseurl}}/img/defaultpage.png)
