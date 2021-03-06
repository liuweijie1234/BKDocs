# 网络管理平台

## 环境准备

1\. 下载 [网络管理平台](https://bk.tencent.com/download_sdk/) :

  - 解压后目录结构如下：

  ```bash
  tree -L 2 /data/src/bknetwork/
  /data/src/bknetwork/
  |-- bknetwork
  |   |-- bin
  |   |-- conf
  |   |-- data
  |   |-- lib
  |   |-- logs
  |   |-- mibs
  |   `-- wwwroot
  |-- INSTALL.md
  |-- MD5
  |-- release.md
  |-- support-files
  |   |-- pkgs
  |   |-- scripts
  |   |-- sql
  |   `-- templates
  `-- VERSION
  ```

2\. 确认蓝鲸社区版的 PaaS，CMDB，JOB 已经部署完成。如无，请参考 [标准部署](../../基础包安装/多机部署/quick_install.md) 进行安装部署。

3\. 解压插件包

```bash
tar xvf bknetwork_ce-3.6.2.tgz -C /data/src/
rsync -a /data/src/install/ /data/install/
```

4\. 修改网络管理相关文件
- 在 install.conf 配置文件中加入 bknetwork。

- 根据实际情况修改中控机 `/data/install/third/globals_bknetwork.env` 网络管理域名等信息。

## 安装部署

  ```bash
  # 假设现 install 目录在 /data/ 下。
  cd /data/install
  # 开始安装
  ./bkco_install bknetwork
  ```

配置的域名访问网络管理，将网络管理平台添加到蓝鲸工作台。


- 通过浏览器登录社区版页面，在域名后添加 `admin` 进入蓝鲸智云后台管理页面。

- 【Home】 - 【常用链接】 - 【增加常用链接】，名称填入网络管理平台，将配置的域名填入链接，类型选择 `SaaS 链接` ，选择 Logo 后保存，即可在蓝鲸工作台中访问 SaaS 网络管理平台。

## 升级更新

1. 停止 bknetwork 服务

```bash
./bkcec stop bknetwork
```

2. 下载最新网络管理软件包

3. 重新部署 bknetwork

```bash
source /data/install/.rcmdrc    # 需要先source .rcmdrc
./bkcec install bknetwork 1
./bkcec start bknetwork
```

