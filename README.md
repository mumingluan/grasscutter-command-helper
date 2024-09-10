# Grasscutter 指令助手

> **Warning**
>
> 本项目采用 [`AGPL-3.0`协议](https://github.com/mumingluan/grasscutter-command-helper/blob/main/LICENSE) 开源, 必须保留本项目版权信息, 禁止倒卖
>
> (你可以随意更改任何内容, 但请一定保留本项目 `Github` 链接)

## [Demo](https://gm.fatui.xyz)

## 前言

基于 [Dituon/grasscutter-command-helper](https://github.com/Dituon/grasscutter-command-helper) fork 并优化更新制成。

## 功能

- 指令生成, 版本切换

- 指令分类, 保存, 分享, 导入

- 远程执行, 账户绑定 (需要 [OpenCommand 插件](https://github.com/jie65535/gc-opencommand-plugin))

- 多语言支持

## GET参数

脚本会解析`URL`中的`GET`参数, 可以向用户提供一些默认值

| 参数      | 值域                              | 说明       |
| --------- | --------------------------------- | ---------- |
| `version` | `1.6.1` `1.4.2` `GM` `1.2.1`      | 指令版本   |
| `lang`    | `navigator.language`              | 语言       |
| `server`  | `encodeURIComponent(URL)`         | 远程服务器 |
| `import`  | `encodeURIComponent(URL)`         | 导入指令   |

**示例**

> `https://gm.fatui.xyz/new?version=1.4.2&server=https%3A%2F%2Fgenshinserver.xmmt.fun%3A25568`
> 
> 指令版本为`1.4.2`, 服务器地址为`https://genshinserver.xmmt.fun:25568`

> `https://gm.fatui.xyz/new?lang=zh-CN&import=./share/artifact.gmh`
>
> 语言为`中文`, 从`/share/artifact.gmh`导入指令

## 部署

### 本地构建

1. `git -clone`

2. `cd ./src`, `npm install`, `npm run build` (使用 [Vite](https://github.com/vitejs/vite))

### 使用 Actions 构建

下载最新版本的 Actions Build Artifact 即可

### 配置 API 反向代理

1. 配置 `Nginx`, 反向代理 `/opencommand` `/status` , 通过 `Header/reqip` 指定目标转发服务器
   
2. `cd ./api` `npm start` 开启 API 服务器

5. 配置 `Nginx`, 代理 `/api` , 将请求转发至 `http://127.0.0.1:1919`（你的 /api 程序的 API Endpoint）



## 更新游戏数据

参见 `/builder/`, 需要 `NodeJS` 环境