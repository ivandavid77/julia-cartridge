# julia-cartridge


Julia Openshift Cartridge



Provide the next URL for cartridge definition when create a new application:
https://raw.githubusercontent.com/ivandavid77/julia-cartridge/master/metadata/manifest.yml

##Example 
The most convenient way for use this cartridge it's using Red-Hat Client (Installation, configuration and further info can be found in https://developers.openshift.com/en/managing-client-tools.html), we'll do next things:
* Create your application
* Login and using julia
* Optionally start the web server and test

#### Create your application
<pre><code>~ $ rhc app create my_project_name https://raw.githubusercontent.com/ivandavid77/julia-cartridge/master/metadata/manifest.yml
Your application 'my_project_name' is now available.
  URL:        http://my_project_name-your_user.rhcloud.com/
  SSH to:     55a5cdf...@my_project_name-your_user.rhcloud.com
  Git remote: ssh://55a5cdf...@my_project_name-your_user.rhcloud.com/~/git/my_project_name
.git/
  Cloned to:  ~/my_project_name
</code></pre>

#### Login and using julia
<pre><code>~ $ rhc ssh my-project-name
Connecting to 55a5cdf...@my_project_name-your_user.rhcloud.com ...
[my_project_name-your_user.rhcloud.com 55a5cdf...]\> julia  # now type julia!
               _
   _       _ _(_)_     |  A fresh approach to technical computing
  (_)     | (_) (_)    |  Documentation: http://docs.julialang.org
   _ _   _| |_  __ _   |  Type "help()" for help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 0.3.10 (2015-06-24 13:54 UTC)
 _/ |\__'_|_|_|\__'_|  |  Official http://julialang.org/ release
|__/                   |  x86_64-unknown-linux-gnu

julia></code></pre>

#### Start web server
From Red-Hat client:
<pre><code>~ $ rhc app start -a my_project_name</code></pre>

Inside openshift instance via ssh:
<pre><code>[my_project_name-your_user.rhcloud.com 55a5cdf...]\> gear start</code></pre>

Test the next urls in your browser:
<pre><code>
http://my_project_name-your_user.rhcloud.com
http://my_project_name-your_user.rhcloud.com/index.html
http://my_project_name-your_user.rhcloud.com/about
http://my_project_name-your_user.rhcloud.com/static/test.html
</code></pre>

By default every file that begins with dot not be showed:
<pre><code>
http://my_project_name-your_user.rhcloud.com/.server.jl   # 403 - Forbidden
</code></pre>

You must edit .server.jl for adding your own content!


##TODO: 
* Enable web sockets in web server and migrate to Morsel
* Make tools for easy deploy for parallel processing in openshift

Suggested by @Ismael-VC:

* preinstall all next packages: https://github.com/JuliaLang/JuliaBox/blob/master/PACKAGES.md 
