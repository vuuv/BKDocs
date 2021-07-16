# 升级指引
本页面为蓝鲸社区版环境下的部署方案变动信息。代码变动及其他部署方式的变动请查阅 [GitHub Release](https://github.com/Tencent/bk-ci/releases) 。

如需迁移微服务到其他主机，请查阅 [维护文档](Maintenance.md) 的 “数据迁移” 章节。

## 流水线（CI）升级指引
### v1.2.x -> v1.5.x
支持直接从灰度体验的 `v1.2.x` 版本升级。
但需先移除openresty目录内的符合链接：
```bash
pcmd -m ci_gateway 'find /usr/local/openresty/nginx/ -maxdepth 1 -type l -delete'
```

引入了新的关键微服务 `dispatch-docker`，必须更新 install.config 文件，请以快速部署文档描述为准。

### v1.2.x -> v1.3.x
v1.3.x 未正式发布，可参考 v1.5.x 更新指引。

## 流水线（CI）部署流程变更记录
部分对接蓝鲸社区版的操作会放在部署流程中更新，部署脚本随代码发布更新。

### 20210706
已在蓝鲸社区版6.0.3测试通过。测试部署的 CI 版本： v1.5.3, v1.5.7。

[下载地址](https://bkopen-1252002024.file.myqcloud.com/bkci/bk-ci-deploy-20210706.dat)
1. 强制安装Tencent KonaJDK。规避部分用户自定义JDK导致的程序异常。[#4591](https://github.com/Tencent/bk-ci/issues/4591)
2. 安装fontconfig，规避v1.5.7版本以下创建项目提示“接口异常”。[#4591](https://github.com/Tencent/bk-ci/issues/4591)

### 20210618
已在蓝鲸社区版6.0.2测试通过。测试部署的 CI 版本： v1.5.3。

[下载地址](https://bkopen-1252002024.file.myqcloud.com/bkci/bk-ci-deploy-20210618.dat)
1. 提前检查java是否存在，安装KonaJDK。
2. 流程全局变量提示文字更新。

### 20210611
已在蓝鲸社区版6.0.2测试通过。测试部署的 CI 版本： v1.5.3。

[下载地址](https://bkopen-1252002024.file.myqcloud.com/bkci/bk-ci-deploy-20210611.dat)

初版。
