<h2>通过LayOtto调用apollo配置中心</h2>

## 快速开始

该示例展示了如何通过LayOtto，对apollo配置中心进行增删改查以及watch的过程。

###部署apollo配置中心并修改LayOtto（可选）

您可以跳过这一步，使用本demo无需自己部署apollo服务器。本demo会使用[apollo官方](https://github.com/ctripcorp/apollo) 提供的演示环境http://106.54.227.205/

如果您自己部署了apollo，可以修改LayOtto的[config文件](../../../../configs/config_apollo.json)，将apollo服务器地址改成您自己的。

###运行LayOtto server 端

将项目代码下载到本地后，切换代码目录、编译：

```bash
cd ${projectpath}/cmd/layotto
go build
```

完成后目录下会生成layotto文件，运行它：

```bash
./layotto start -c ../../configs/config_apollo.json
```

###启动客户端Demo，调用LayOtto增删改查

```bash
 cd ${projectpath}/runtime/demo/configuration/apollo
 go build -o apolloClientDemo
 ./apolloClientDemo
```

打印出如下信息则代表调用成功：

```bash
save key success
get configuration after save, &{Key:key1 Content:value1 Group:application Label:prod Tags:map[feature:print release:1.0.0] Metadata:map[]} 
get configuration after save, &{Key:haha Content:heihei Group:application Label:prod Tags:map[feature:haha release:1.0.0] Metadata:map[]} 
delete keys success
write start
receive subscribe resp store_name:"apollo" app_id:"apollo" items:<key:"heihei" content:"heihei1" group:"application" label:"prod" tags:<key:"feature" value:"haha" > tags:<key:"release" value:"16" > >
```

###拓展

示例客户端Demo中使用了LayOtto提供的golang版本sdk，sdk位于runtime/sdk目录下，用户可以通过对应的sdk直接调用LayOtto提供的服务。
