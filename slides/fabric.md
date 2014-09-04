# Fabric
* python
* not strictly a deployment tool - execute any Python functions via cli as well as shell commands via ssh


```
env.hosts = ['xxx.xxx.xxx.xxx', 'xxx.xxx.xxx.xxx']
env.user = 'rockfish'

def deploy():
    code_dir = '/home/rockfish/fabric/webroot/'
    with cd(code_dir):
        run("git pull")
```

To Execute:

```
fab deploy
```
