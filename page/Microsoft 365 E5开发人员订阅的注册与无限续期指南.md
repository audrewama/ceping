# Microsoft 365 E5开发人员订阅的注册与无限续期指南

![Microsoft 365 E5](https://bbtdd.com/img/646129776010.webp)

微软的Microsoft 365 E5开发人员订阅，每个账号可以开通25个子账号，每个子账号都能免费使用Office套件和5T的OneDrive云存储，非常实用。本文将详细介绍如何注册、续期以及相关注意事项，助你实现无限白嫖。

## 当前版本的E5账号注册流程

由于Office 365已更名为Microsoft 365，注册流程和页面也发生了相应变化。以下是当前版本的注册步骤：

1. 访问 **Microsoft 365 开发人员计划** 的注册入口：[https://developer.microsoft.com/zh-cn/microsoft-365/dev-program](https://developer.microsoft.com/zh-cn/microsoft-365/dev-program)。
2. 注册时需注意：
   - 使用一个未申请过开发者订阅的微软账号和手机号（+86即可）。
   - 数据中心的国家地区选择“Singapore”，以优化国内访问速度。

注册完成后，你将直接获得90天的E5订阅，接下来是使用和维护的步骤。

## 创建子账号

1. 登录微软账号管理页面：[https://admin.microsoft.com/](https://admin.microsoft.com/)。
2. 使用E5订阅的管理员账号登录，格式为“[email protected]”。
3. 在用户管理选项卡中创建子账号，建议创建一个备用账号，方便后续使用挂机程序。
4. 创建时请勾选“Microsoft 365 E5 开发者”许可证。

## 将OneDrive存储空间从1T升级至5T

1. 登录OneDrive企业版控制台页面：[https://admin.onedrive.com/](https://admin.onedrive.com/)。
2. 点击右上角小方块，选择“设置”，找到“OneDrive 存储限制”。
3. 将存储限制修改为5120GB，此设置对所有子账号生效。

## 在Azure创建API应用以续签订阅

1. 使用E5订阅的管理员账号登录Azure的AD服务。
2. 在“应用注册”中，选择“+ 新注册”。
3. 填写应用名称，选择“任何组织目录中的帐户和个人 Microsoft 帐户”作为受支持的账户类型，重定向URI类型选择“Web”，域名无需填写。
4. 创建后，在“身份验证”中添加平台，选择“移动和桌面应用程序”，配置重定向URI。
5. 复制并保存应用的“应用程序ID”。

完成以上设置后，禁用安全默认值以防止挂机脚本掉线。

## 推荐的续签软件

- **M365 E5 Renew Plus**（PC端）：[https://e5renew.com/](https://e5renew.com/)
- **Microsoft 365 E5 Renew X**（Docker端）：提供x86和arm版本镜像

使用这些软件时，只需填入子账号和应用ID即可运行。建议长期挂机以确保续签成功。

👉 [WildCard | 一分钟注册，轻松订阅海外线上服务](https://bbtdd.com/WildCard)

## 注意事项

挂机程序在订阅剩余30天时尝试续签，但成功率并非100%。虽然成功率较高，但仍有翻车风险，建议不要在账号上存储重要数据，并多备份。