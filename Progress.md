#### 关于5年长期计划
- 做有价值的事情
- 看清趋势，积累用户。
- 垂直行业。
- 用1年的时间来思考。
- 做好充分调研

#### Mac Nginx  
- 安装nginx服务：brew install nginx
- 启动nginx服务： sudo nginx
- 重新加载配置|重启|停止|退出： nginx -s reload|reopen|stop|quit
- 测试配置是否有语法错误： nginx -t
- 配置文件路径：/usr/local/etc/nginx/nginx.conf
- 自己的conf可以加到servers目录下

#### Mac PHP 安装
- 参考 https://segmentfault.com/a/1190000005090828
- 配置环境变量：PATH="/usr/local/sbin:$PATH"
- 操作命令：sudo php56-fpm {start|stop|force-quit|restart|reload|status}
- php.ini位置：/usr/local/etc/php/5.6
- php-fpm.conf位置：/usr/local/etc/php/5.6

#### Mac Mysql配置
- 配置文件路径：/usr/local/Cellar/mysql/
- mysql.server start|stop|status #启动|停止|状态
- 设置密码：/usr/local/bin/mysqladmin -u root password 'new-password'
- 连接mysql：mysql -uroot -p

#### &#65279 编码问题
- 将页面编码保存为utf-8格式即可，然后revome BOM

#### json解析
- JSON.stringify() object-->str
- JSON.parse()  str-->object

#### git stash
- 保存工作区： git stash save "desc"
- 显示列表： git stash list
- 恢复工作区：git stash pop
- 恢复指定save： git stash pop stash@{序号}

#### iterm2 快捷键
- 新建分屏 command+D
- 关闭分屏 command+W

#### 冲突解决
git解决冲突之后，git add file... 

#### mac上传文件到ubuntu 
scp /path/filename ubuntu@servername:/path 

#### 二级域名配置
- 阿里云配置二级域名IP指向
- nginx配置项目root

#### Pixolor 一个android屏幕取色工具  
https://www.appinn.com/pixolor-for-android/  

#### mysql 远程访问
然后打开vim  /etc/mysql/my.cnf  
将bind-address    = 127.0.0.1  
设置成bind-address    = 0.0.0.0（设备地址）  


#### fiddler
学习了抓包工具fiddler的使用。


