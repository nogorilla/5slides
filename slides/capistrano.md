# Capistrano
* ruby
* remote server automation and deployment
* uses a pre-defined folder structure, requires setup command


```

| current  
| releases  
|	|-- 201401010100  
|	|-- 201312310800
```	


```
set :branch, "master"

set :application, "camel-mobile"
set :scm, :git
set :scm_verbose, true
set :use_sudo, true
set :repository,  "git@github.com:RockfishInteractive/RJReynolds_Camel_mweb.git"
set :keep_releases, 5
set :user, "deploy"
set :owner, "apache"
set :group, "apache"
set :repository,  "git@rfd0git01:/var/git/camel_mobile.git"
set :use_sudo, true
set :keep_releases, 5

default_run_options[:pty] = true

ssh_options[:forward_agent] = true
ssh_options[:port] = 22
ssh_options[:keys] = '../../../id_rsa_deploy'

role :app, "xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx"

after "deploy:restart", "deploy:cleanup"

namespace :deploy do
  desc "Deploys code to environments"
  task :restart do
    sudo "chown #{owner}:#{group} -R #{deploy_to}"
    sudo "cp #{http_conf_new} #{http_conf_old}"
    sudo "cp #{http_reqconf_new} #{http_reqconf_old}"
    sudo "/etc/init.d/httpd restart"
  end
end
```
To Execute:
```
cap production deploy
```
