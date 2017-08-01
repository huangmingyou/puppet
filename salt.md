1. 服务器配置使用 单机 模式的 saltstack 的 state 来保障服务应用处于正确的配置状态。

2. saltstack 配置文件通过deb包 vsalt 分发。 sls代码安装到 /opt/salt ; 用 salt-call –local state.highstate 调用。

3. 每服务器的区别配置，主要通过 saltstack 的 grains 来定义不同的变量。

4. grians 保存到 /etc/vsalt.conf ; 由脚本 ldap2grains.sh 查询openldap 自动生成。

5. openldap 里面，主机在 ou=datacenter,dc=example,dc=cn 下面。

6. 主机可以定义一组角色， 每组角色会定义一些grains值

7. 角色可以是定义一组应用的配置，例如nginx,zabbix,mysql ; 也可以定义一个机房的配置，例如该机房里面的zabbix 服务器地址，redis地址等信息。

8. ldap2grains.sh 脚本会查询host属于那个datacenter,找到该datacenter的角色定义，同时也查询host的VPhotosRole属性来看host定义了那些角色。
