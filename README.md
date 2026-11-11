# 项目来信

面向软件开发需求收集的独立网站：客户提交需求，管理员登录后查看、搜索、分页并记录跟进。界面使用 React、shadcn/ui 和 AG Grid Community；数据与认证使用 Supabase。

## 本地运行

```sh
npm ci
npm run dev
```

客户页面：http://127.0.0.1:5178/；管理入口：http://127.0.0.1:5178/?view=admin。生产配置中的 Supabase URL 和 publishable key 是公开客户端配置，访问权限由 Supabase RLS 控制；不要将 service role / secret key 放入仓库或前端。

## 部署与数据

GitHub Actions 将站点发布到 GitHub Pages 的 `/project-inquiry/` 路径。静态网站托管在 Pages，数据和认证使用现有云端 Supabase 项目内独立的线索表和管理员白名单。数据库脚本位于 `supabase/migrations`；当前云端已单独应用此脚本，它未记录在原电商项目的常规迁移历史中。管理员账户需在 Supabase Auth 创建并授权至 `lead_studio_admins`。

当前自动通知和联系方式尚未配置，数据库有两条标记为测试的虚构需求。正式运营前需要配置通知及联系方式，并完善防滥用、备份和隐私说明。各平台接入边界和方案调研见 [research.md](research.md)。
