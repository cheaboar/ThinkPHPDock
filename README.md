# ThinkPHPDock

### 说明
ThinkPHPDock使用的docker搭建开发环境，参考laradock的部分文件格式，添加Ubuntu和Debian的apt-get阿里源和网易源。可以通过docker-compose指令快速启动。
暂时添加了php-fpm, mysql, nginx，后期加入redis和memchache等服务。

### 使用

启动nginx服务器和MySQL服务器。
```
docker-compose up -d nginx mysql
```
使用docker-compose up 才可启动端口映射，docker-compose run不进行端口映射。

#### 包含有以下内容
- PHP5.6
- Mysql
- Ubuntu
- nginx
