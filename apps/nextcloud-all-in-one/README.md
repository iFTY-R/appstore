# Nextcloud All-in-One

**Nextcloud All-in-One** （简称 AIO）是一套由官方提供的“一体化” Docker 解决方案，集成了 Nextcloud 核心及其常用组件（数据库、Redis、Talk 等），可以通过一行命令快速启动并进行配置。

## 特点

- 官方维护的镜像，一键部署所有组件
- 支持内置自动更新、备份、ClamAV、全套办公套件等功能
- 默认端口：Web 控制面板 8080，Nextcloud 服务 11000（需反向代理）
- 推荐宿主机配置：2 vCPU、≥3 GB 内存

## 使用说明

1. **克隆本地应用到 1Panel 目录**
   将本文件夹 `nextcloud-all-in-one/` 整体复制到 `/opt/1panel/resource/apps/local/`

2. **更新应用列表**
在 1Panel 后台进入“应用商店 → 更多 → 本地”，点击“更新应用列表”，即可看到“Nextcloud All-in-One”应用。

3. **点击安装**
选择版本 `latest`，点击“安装”后，1Panel 会自动拉取镜像、创建容器并启动。

4. **访问 AIO 控制面板**
安装完成后，Nextcloud AIO 主容器的管理界面默认映射到宿主机 `8080` 端口。
例如：`http://<你的服务器 IP>:8080`
进入后可根据提示配置域名、证书和额外模块的安装。

5. **反向代理（可选）**
若要通过域名访问 Nextcloud，需要在宿主机上使用 Nginx/“反向代理”将外部请求转发到内部 `127.0.0.1:11000`。
详细配置请参考[官方文档](https://github.com/nextcloud/all-in-one/blob/main/reverse-proxy.md)。

---

## 常见问题

- **为什么要用 AIO 而不是手动部署？**
AIO 集成了数据库、Redis、BorgBackup 等组件，省去手动安装和性能调优的繁琐步骤；当需要扩展时也可在 AIO 控制面板中一键安装 Nextcloud Talk、Full-text Search、ClamAV 等模块。

- **宿主机资源不够怎么办？**
AIO 对资源要求较高，建议至少 2 vCPU、≥3 GB 内存。若资源不足，可考虑手动分离部署单独的 Nextcloud 主容器和数据库容器。

- **如何升级到新版本？**
直接在 1Panel 中进入本地应用商店，点击“更新应用列表”，如果有新的文件夹（如 `latest`），则可将其版本目录添加到 `nextcloud-all-in-one/` 下，然后更新应用列表并选择该版本安装。

