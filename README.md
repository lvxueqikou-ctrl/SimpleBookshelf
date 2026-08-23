# SimpleBookshelf

KOReader 书架管理插件，独立安装，可选接入 SimpleUI 导航栏。

## 功能

- 立体书脊式书架展示、分页和排序
- 单本书外观和书脊图片设置
- 全局书架样式、排序、书籍目录和壁纸设置
- 上传、更换书脊图片
- 通过二维码在手机浏览器上传书脊图片
- 可选 WebDAV 共享库，用于跨设备调用已经上传的书脊图片
- 顶部下滑打开 KOReader 原生菜单
- 延迟加载和局部刷新，减少内存峰值与卡顿

## 安装

将 simplebookshelf.koplugin 整个文件夹复制到 /mnt/us/koreader/plugins/。

最终路径应为 /mnt/us/koreader/plugins/simplebookshelf.koplugin/main.lua。

重启 KOReader 后，在 SimpleUI 或 KOReader 插件菜单中打开 SimpleBookshelf。

## SimpleUI 兼容

SimpleBookshelf 可以独立运行，也可以接入 SimpleUI 导航栏。SimpleUI 不会被打包进本插件，用户需要自行安装 SimpleUI。

插件通过兼容桥接调用 SimpleUI 的导航栏和配置接口，兼容 SimpleUI 2.1.1 与 2.5.0。未安装 SimpleUI 时，插件会使用独立页面模式。

## 二维码上传

在书籍编辑页面选择二维码上传。手机和 Kindle 必须连接到同一个局域网。二维码使用设备当前网络地址生成，不包含固定 IP，换网络后重新生成即可。

部分公共 Wi-Fi 会启用客户端隔离，导致手机无法打开 Kindle 提供的上传页面。此时应改用电脑热点或家庭局域网。

## WebDAV 共享库

插件使用当前设备 KOReader 中已经配置的 WebDAV 账号，不写死账号、密码或服务器地址。启用共享库后，可在书籍编辑页面选择“从共享库调用”。

## 操作入口

- 在书脊上长按：打开当前书籍的外观、书名显示、书脊图片和裁切设置。
- 在空白区域长按：打开全局设置，包括书架行数、立体度、边距、字号、排序、书籍文件夹和壁纸。

当前版本不提供批量移动、批量删除、批量重命名，也不提供编辑书名、作者等书籍元数据的入口。

## 兼容性

- KOReader 当前稳定版本
- SimpleUI 2.1.1
- SimpleUI 2.5.0
- Kindle Scribe、Kindle Paperwhite 等已测试设备

## 许可证

本项目采用 GNU Affero General Public License v3.0，完整文本见 LICENSE 文件。

KOReader 本体和相关官方插件集合采用 AGPL-3.0。本仓库不包含 SimpleUI 本体；SimpleUI 是可选的外部依赖，请按照其自身仓库的许可证和说明使用。

## 注意事项

- 不要将个人 WebDAV 配置、SSH 信息、IP 地址、日志或个人书籍提交到仓库。
- 二维码上传和共享库只传输书脊图片，不会上传书籍正文。
- 建议使用尺寸适中的 JPG 或 PNG，过大的图片可能造成电子墨水设备短暂卡顿。

## 目录结构

simplebookshelf.koplugin/
├─ main.lua
├─ spine_upload.lua
├─ spine_cloud.lua
├─ simpleui_bridge.lua
├─ _meta.lua
└─ bookshelf.svg
