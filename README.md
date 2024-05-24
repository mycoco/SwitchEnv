# SwitchEnv
> 基于浏览器流量,将DNS解析规则提升到应用层

1. 浏览器安装 SwitchyOmega 插件
2. 配置 SWitchEnv 监听的端口
3. 解析域名的规则由 SWitchEnv 接管

#### 解析规则
1. 首先,查询域名与ip映射关系
    - 优先查找 单个域名与ip的匹配
    - 其次根据 模糊匹配进行查找
2. 其次,根据匹配条件,使用指定DNS进行解析
3. 最后,使用操作系统的DNS进行解析


#### Env List 
> 可以配置多条解析规则,使用不同的端口

#### 新增/修改配置
1. 方案名称, 用于区分规则名称
2. 监听端口, 用于隔离浏览接管
3. 域名IP映射关系, 可以实现ip与域名直接映射 
> 类似修改操作系统的 hosts 文件
4. 指定DNS解析
> 在[域名与IP映射关系]中未找到域名对应的IP后则使用指定DNS来解析
* 匹配条件, * 所匹配的域名江使用 [指定DNS] 进行解析,
- 匹配条件[*],代表所有域名
- 匹配条件[*abc001.com],代表所有abc001.com域名
- 匹配条件[*abc001.com;*abc002.com],代表所有abc001.com以及abc002.com域名
如果不满足匹配条件的,则使用操作系统的默认DNS进行解析


#### 域名IP映射关系 规则说明 

1. 注释行
```
#这是注释
192.168.100.51 www.abc001.com  #行内尾部写注释
```

2. 单个域名与ip匹配
> 解析 www.abc111.com 的 ip 为 192.168.100.51
```
192.168.100.51  www.abc111.com
```

3. 多个域名与ip匹配, 多个域名之间使用分号或逗号分隔
> 解析 www.abc111.com 和 www.abc112.com 的 ip 为 192.168.100.51
```
192.168.100.51  www.abc111.com;www.abc112.com
```

3. 单个模糊匹配
> 所有 abc112.com 后缀域名的 ip 为 192.168.100.52
```
192.168.100.52  *abc112.com
```

4. 多个模糊匹配, 多个匹配规则使用分号或逗号分隔
> 所有 abc112.com 和 abc113.com 后缀域名的 ip 为 192.168.100.52
```
192.168.100.52  *abc112.com;*abc113.com
```

#### DNS List 可以预设多条DNS服务器地址

#### About  关于



