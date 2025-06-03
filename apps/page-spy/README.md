# PageSpy 1Panel 应用

> **页面监控与抓取工具**  
> 一个基于 Web 的页面监控和数据抓取应用，通过 1Panel 一键部署，无需手动执行 Docker 命令。

## 功能概览

- **定时监控**：对指定网页内容变化进行比对并展示。
- **数据抓取**：将 HTML/JSON 数据保存到 `./data` 目录，并可在界面或 API 下载。
- **权限控制**：通过表单填写 `AUTH_PASSWORD` 登录管理界面；使用 `JWT_SECRET` 和 `JWT_EXPIRATION_HOURS` 管理会话。
- **持久化存储**：日志保存在宿主机 `./log`；抓取数据保存在 `./data`。
- **一键部署**：在 1Panel 中上传目录，填写表单后自动生成并启动容器。

---

## 快速安装

1. 将整个 `page-spy` 目录上传到 1Panel。
2. 选择版本（如 1.0.0），点击「安装」。
3. 填写：
   - **认证密码（AUTH_PASSWORD）**
   - **JWT 密钥（JWT_SECRET）**
   - **JWT 过期时间（JWT_EXPIRATION_HOURS，单位：小时）**
4. 完成后，通过 `http://<面板地址>:6752` 访问 PageSpy，输入密码登录即可。

---

## 常见说明

- **日志目录**：容器内 `/app/log` 映射到宿主机 `./log`。
- **数据目录**：容器内 `/app/data` 映射到宿主机 `./data`。
- **端口**：默认映射 `6752:6752`，可在版本 `data.yml` 中添加 `PANEL_APP_PORT_HTTP` 自定义外部端口。

---

## 参考链接

- 应用官网与文档：<https://www.pagespy.org/#/docs/introduction>
- 源码仓库：<https://github.com/huolalatech/page-spy-web>  
