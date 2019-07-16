#############提交日期 2019-7-16

注意：这个版本是按照分支来获取代码的，主要是针对php代码的，包括发布和回滚功能，如果是java环境，则需要增加一个编译代码的环节


1 如果主机未发布过，是不能回滚的，就是不能看到他的版本

2 创建项目的时候，项目的名字要和你giturl后面的那个名字一致

3 在windows上面如果点击获取代码的时候，应该会报拒绝访问，这是因为删除的命令不能在windows上面生效，需要你手动删除codes目录下面的所有代码

4 用了rbac基于角色的权限管理

5 新增了发布和回滚的时候有图标转动提醒

6 发布和回滚主要是借用rsync去实现的，把下载下来的代码拷贝到nginx对应的目录下面

7 需要在对应的用户里面配置私钥，和gitlab的用户名和密码，用于下载代码和连接主机，（项目部署到那台机器，就用那台机器的私钥，并且把这台机器的公钥，放到所有要发布机器的authorized_key文件里面

8 发布到线上的脚本是在/home/yx/script/PHP  这个目录下面，根据日期来定文件夹的名字，发布到线上的脚本在/home/yx/codes/PHP/  也是根据日期来定文件夹的名字

9 回滚的脚本是在/home/yx/rollback_script/PHP，同样根据日期来命名，而回滚的代码就是用的，发布代码目录下面的代码去实现回滚的，目录根据自己的情况来定

10 增加了针对整个分支合单文件的不同发布

11 增加了判断分支是否合并到主干的功能，如果没有会弹出一个弹框提示你



##########################需要安装的模块

PIL 就是pillow模块
requests   pip install --user requests
paramiko
bs4

#######################################

django后台用户名密码：

admin
root1234
添加用户登录django后台操作

##########################各个角色用户名密码auth_user

管理员  admin 123
开发  kf 123
项目负责人 project 123
运维  hu 123
测试  cs 123
产品 pm 123

#############################




写一个专门发布单文件的脚本，只同步这个文件，但是单文件是个变量，想办法把web页面的单文件名字，给放到一个单独的文件里面
写一个专门发布整个分支的脚本，排除一些配置文件，其余的全部同步，



如果在同一个分支，两次更新代码，在执行脚本的时候，会提示你是否覆盖，需要手动操作

判断分支是否合回主干，前提是必须进入到项目的目录里面执行git log --merges命令，查看合并记录
