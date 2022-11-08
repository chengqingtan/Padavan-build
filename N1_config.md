# N1旁路由配置教程

本教程不需要修改主路由，但需要在为每个需要用到旁路由的客户端配置网关和DNS

## 主路由环境

主路由为 openwrt-21.02 or openwrt-22.03，已配置 **IPv6 NAT** ，lan口IP为 **192.168.1.1** 和 **fc00:101:101:1** 

## 配置旁路由

1. 删除N1的 **wan** 和 **wan6** 

2. 防火墙自定义规则内添加以下一行后重启防火墙

   ```
   iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE
   ```

3. 修改 **lan** 口，协议选择 **静态协议** ，IP填写 **192.168.1.x** ，网关和DNS都填写 **192.168.1.1** ，勾选 **不在此接口上提供DHCP服务** 

## 配置旁路由IPv6

1. 关闭 **lan** 口内的IPv6配置
2. 删除 **IPv6 ULA** 前缀
3. 新建一个 **lan6** 口，协议选择 **DHCPv6** ，接口新建一个自定义接口 **@lan6** 
4. **lan6** 口关闭内置的IPv6管理，防火墙选择 **lan**
5. 取消勾选 **禁止解析 IPv6 DNS 记录**

## 注意事项：

1. 不需要 **重设Mac地址** ，Mac地址重复容易引起问题
2. 在旁路由上配置 **L2TP** 后无法上网