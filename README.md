# I Hate Money 懒猫微服包

自托管的分账工具：和朋友平摊账单，看清谁欠谁多少。

- 上游：<https://github.com/spiral-project/ihatemoney>
- 镜像：`ihatemoney/ihatemoney`
- 许可：BSD-3-Clause（全文见 content/licenses/LICENSE，无子目录覆盖条款）

## 组成

单容器，监听 8000 端口，内置 SQLite，无需外部数据库。

## 关键配置说明

- **`SECRET_KEY` 必须覆盖**：上游示例里是字面量 `tralala`（会话与 CSRF 令牌依赖它）。
- `SQLALCHEMY_DATABASE_URI=sqlite:////database/ihatemoney.db`：内置 SQLite，
  数据库文件落在挂载目录 `/lzcapp/var/database` 上。
- **全局管理面板默认关闭**（`ACTIVATE_ADMIN_DASHBOARD=False` + 空 `ADMIN_PASSWORD`）：
  它是一个跨所有项目的共享密码入口，不需要就不开。
- **不需要注册**：参与者通过项目链接加入，因此**不加 `public_path`**，
  访问由懒猫入口鉴权。

## 未验证部分

未在真机上实测：创建项目、添加支出、分摊计算、导出、重启后数据留存。
