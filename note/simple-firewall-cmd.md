# firewall-cmd简明教程

## firewall-cmd服务

* 查看服务状态: `systemctl status firewalld.service`
* 开启服务: `systemctl start firewalld.service`
* 关闭服务: `systemctl stop firewalld.service`
* 开机自启服务: `systemctl enable firewalld.service`
* 关闭开机自启服务: `systemctl disable firewalld.service`

## firewall-cmd查询

* 查看firewall帮助: `firewall-cmd --help`
* 查看firewall状态: `firewall-cmd --state`
* 查看firewall信息: `firewall-cmd --list-all`
* 查看激活的区域: `firewall-cmd --get-active-zones`
* 获取所有支持的服务: `firewall-cmd --get-service`
* 查看http服务启动状态: `firewall-cmd --query-service http`
* 查看public区域的永久开启的服务: `firewall-cmd --permanent --zone=public --list-services`
* 查看public区域的永久开放的端口: `firewall-cmd --permanent --zone=public --list-ports`
* 查看public区域的永久使用的富规则: `firewall-cmd --permanent --zone=public --list-rich-rules`

## firewall-cmd设置

* 在public区域永久启用http服务: `firewall-cmd --permanent --zone=public --add-service=http`
* 在public区域永久禁用http服务: `firewall-cmd --permanent --zone=public --remove-service=http`
* 在public区域永久开放8080tcp端口: `firewall-cmd --permanent --zone=public --add-port=8080/tcp`
* 在publice区域永久开放8080-8090段tcp端口: `firewall-cmd --permanent --zone=public --add-port=8080-8090/tcp`
* 在public区域永久关闭8080tcp端口: `firewall-cmd --permanent --zone=public --remove-port=8080/tcp`
* 永久使用富规则以允许192.168.1.2ipv4访问: `firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="192.168.1.2" accept'`
* 永久使用富规则以允许192.168.1.0/24ipv4访问: `firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="192.168.1.0/24" accept'`
* 永久使用富规则以丢弃192.168.1.2ipv4访问: `firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="192.168.1.2" drop'`
* 永久使用富规则以禁止192.168.1.2ipv4访问: `firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="192.168.1.2" reject'`
* 永久删除允许192.168.1.2ipv4访问的富规则: `firewall-cmd --permanent --remove-rich-rule='rule family="ipv4" source address="192.168.1.2" accept'`
* 重载firewall-cmd配置以使新配置生效: `firewall-cmd --reload`
