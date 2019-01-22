[inception文档地址](https://github.com/bbotte/inception-document)

在数据库给inception设置授权

```
grant all on *.* to 'inception'@"%" identified by "123456";
flush privileges;
```

设置后，配置inc.cnf,里面inception几项配置必须可以访问数据库

```
inception_remote_backup_host=127.0.0.1 
inception_remote_backup_port=3306 
inception_remote_system_user=inception
inception_remote_system_password=123456
```

```
nohup ./bin/Inception --defaults-file=./inc.cnf &
```
```
./bin/mysql -uroot -h127.0.0.1 -P6669
inception get variables;
```

关于inc.cnf配置中inception_osc配置，打开的话需要安装percona toolkit工具

[percona-toolkit下载](https://www.percona.com/downloads/percona-toolkit/LATEST/)

```
yum localinstall percona-toolkit-3.0.10-1.el7.x86_64.rpm
```
