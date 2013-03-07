RubyOnRailsTrains
=================

RubyOnRails开发实践

1、下载安装Ruby(http://rubyforge.org/frs/?group_id=167); 
2、查看版本，并进行更新；
   ruby -v #查看ruby版本号
   gem -v #查看Gem版本号
   gem update --system  #更新Gem
3、远程下载安装Rails；
   gem install rails --remote
4、更新开发用到的组件,可以用gem list查看已经安装的组件列表。
如：gem install jquery-rails
    gem install mysql
    gem install sqliet3
    gem install sqlite3-ruby
gem list列表：
    actionmailer (3.2.12)
    actionpack (3.2.12)
    activemodel (3.2.12)
    activerecord (3.2.12)
    activeresource (3.2.12)
    activesupport (3.2.12)
    arel (3.0.2)
    igdecimal (1.1.0)
    builder (3.0.4)
    bundler (1.3.1)
    cgi_multipart_eof_fix (2.5.0)
    coffee-rails (3.2.2)
    coffee-script (2.2.0)
    coffee-script-source (1.6.1)
    erubis (2.7.0)
    execjs (1.4.0)
    gem_plugin (0.2.3)
    git (1.2.5)
    hike (1.2.1)
    i18n (0.6.4)
    io-console (0.3)
    journey (1.0.4)
    jquery-rails (2.2.1)
    json (1.5.5)
    mail (2.4.4)
    mime-types (1.21)
    minitest (2.5.1)
    mongrel (1.1.5 x86-mingw32)
    multi_json (1.6.1)
    mysql2 (0.3.11 x86-mingw32)
    pg (0.14.1 x86-mingw32)
    polyglot (0.3.3)
    rack (1.4.5)
    rack-cache (1.2)
    rack-ssl (1.3.3)
    rack-test (0.6.2)
    rails (3.2.12)
    railties (3.2.12)
    rake (10.0.3, 0.9.2.2)
    rb-readline (0.4.2)
    rdoc (3.9.5)
    rubygems-update (2.0.2)
    rubyzip (0.9.9)
    sass (3.2.6)
    sass-rails (3.2.6)
    sprockets (2.2.2)
    sqlite3 (1.3.7 x86-mingw32)
    sqlite3-ruby (1.3.3)
    thor (0.17.0)
    tilt (1.3.5)
    tiny_tds (0.5.1 x86-mingw32)
    treetop (1.4.12)
    tzinfo (0.3.36)
    uglifier (1.3.0)
5、安装部署Mongrel服务器；
1）、下载并进行安装：gem install mongrel,gem install mongrel_service
2）、把Mongrel作为Services启动
3）、把Mongrel作为Services启动
mongrel_rails service::install -N ent -d D:\HelloWorld -p 3000 –e production
-N指明服务名称，-d指明rails应用的目录，-p是mongrel监听的tcp端口，-e是启动模式为生产模式
在命令行里面，运行会提示安装成功。
4）、打开控制面板-》管理工具-》服务里面，会找到ent这个服务名称，ent就是前面第3不输入的步骤，启动这个服务就可以，当然可以设置为自动启动（确实情况下是手工启动）
5）、服务的删除和停止
mongrel_rails service::stop -N ent
如果需要从服务中注销该项服务，那么：
mongrel_rails service::remove -N ent
如果需要安装多个mongrel实例，那么可以这样：
mongrel_rails service::install -N ent0 -c D:\HelloWorld -p 3000 –e production
mongrel_rails service::install -N ent1 -c D:\HelloWorld -p 3001 –e production
6）、其实现在就可以用http://localhost:3000来访问Rails程序了。
7）、可以用Apache的Proxy功能，来把向本机80的请求转发到3000端口，实现Rails的发布。
配置如下在httpd.conf里面进行修改，去掉下面三行前面的注释（#):
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_balancer_module modules/mod_proxy_balancer.so
LoadModule proxy_http_module modules/mod_proxy_http.so
如果你希望对页面输出使用压缩，也需要取消如下模块的注释：
LoadModule deflate_module modules/mod_deflate.so
最后加入：
ProxyRequests Off
<Proxy balancer://myCluster>
BalancerMember http://localhost:3000
BalancerMember http://localhost:3001
>
<VirtualHost *:80>
ServerName www.xxx.com
DocumentRoot d:/rubyproject/depot/public
ProxyPass /images !
ProxyPass /stylesheets !
ProxyPass /javascripts !
ProxyPass / balancer://myCluster/
ProxyPassReverse / balancer://myCluster/
ProxyPreserveHost on
>

  [john gruber]: http://daringfireball.net/
  [@thomasfuchs]: http://twitter.com/thomasfuchs
  [1]: http://daringfireball.net/projects/markdown/
  [showdown]: https://github.com/coreyti/showdown
  [ace editor]: http://ace.ajax.org
  [node.js]: http://nodejs.org
  [Twitter Bootstrap]: http://twitter.github.com/bootstrap/
  [keymaster.js]: https://github.com/madrobby/keymaster
  [jQuery]: http://jquery.com  
  [@tjholowaychuk]: http://twitter.com/tjholowaychuk
  [express]: http://expressjs.com
