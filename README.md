 # Grok Playground Deno Deploy 部署说明书

**程序作者:** guhaochong

------



## 项目概述

Grok Playground 是一个代理服务应用，允许用户通过 Deno Deploy 部署的服务访问 Grok AI 服务。该项目通过转发请求到官方 Grok 服务器，同时处理必要的认证和资源替换，使用户能够在国内环境中无需魔法使用 Grok 的功能。

## 部署到 Deno Deploy

### 前提条件

1. 拥有 [GitHub](https://github.com/) 账号
2. 拥有 [Deno Deploy](https://deno.com/deploy) 账号（可使用 GitHub 账号登录）

### 部署步骤

1. **新建项目仓库**
   - 将 **`src`** 文件夹 放到你的新仓库中，并且编辑修改 **`src/static/users.json`** 中的变量
2. **登录 Deno Deploy**
   - 使用 GitHub 账号登录 [Deno Deploy](https://deno.com/deploy)
3. **创建新项目**
   - 点击 "New Project" 按钮
   - 选择 "Deploy from GitHub"
   - 选择新建的仓库
4. **配置部署设置**
   - 选择分支（通常是 `main` 或 `master`）
   - 入口文件设置为 `src/deno_index.ts`
   - 环境变量：无需特别设置，除非有自定义需求
5. **完成部署**
   - 点击 "Deploy" 按钮
   - 等待部署完成，Deno Deploy 会提供一个 `*.deno.dev` 域名

## 使用方法

### 访问部署的应用

1. 编辑 **users.json** 中的变量。**注意**，所有内容都需要使用 **Base64编码** 后才能使用。

     | 变量     | 定义                                |
     | -------- | ----------------------------------- |
     | password | 登录密码（默认登录密码为 **123** ） |
     | username | 显示的账户名                        |
     | cookie   | Gork登录后的浏览器cookies           |

     ```json
     {
     "password": "MTIz",
       "users": [
     {
       "username": "此处替换为显示的账户名",
       "cookie": "此处替换为Gork登录后的浏览器cookies"
     }
       ]
     }
     ```

     

2. 
     使用 Deno Deploy 提供的域名访问应用（例如：`https://your-project-name.deno.dev`）

3. 使用 `123` 密码登录后，选择指定的账号即可使用 Grok 功能

4. 支持多账户切换使用，请自行添加相应变量即可

### Cookie 获取方法

1. 访问官方 Grok 网站并登录
2. 打开浏览器开发者工具（F12）
3. 在网络或应用标签页中找到 cookie 信息
4. 复制 grok_cookie 的值
5. 将此值粘贴到 Grok Playground 的相应设置中

## 注意事项

1. Deno Deploy 免费计划有一定的使用限制，请查阅官方文档了解详情
2. 该项目仅用于个人学习和研究目的，本人不提供任何技术支持
3. 使用时需遵守 Grok 的服务条款
4. 本项目参考 技术爬爬虾 开源文档

