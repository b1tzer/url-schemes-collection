# URL Schemes Collection

一个精选的热门应用 URL Scheme 集合（涵盖 iOS、Android、macOS 等），以 JSON 格式存储。便于查询和集成应用专属深度链接，适用于自动化、快捷指令或开发场景。

## 功能特点

- **多平台支持**：涵盖 iOS、Android、macOS 等主流平台
- **热门应用**：收录常用社交、工具、娱乐等各类应用
- **详细参数**：提供每个 URL Scheme 的参数说明和使用示例
- **结构化数据**：采用清晰的 JSON 格式，便于程序解析和使用
- **持续更新**：定期维护和更新最新的应用 URL Scheme

## 数据结构

JSON 文件按照平台分类组织，包含以下主要字段：

### iOS/Android 应用
- `app_name`：应用名称
- `bundle_id`/`package_name`：应用包名
- `scheme`：URL Scheme 前缀
- `description`：Scheme 描述
- `parameters`：可用参数列表
- `example`：使用示例

### macOS 应用
- `app_name`：应用名称
- `bundle_id`：应用包标识符
- `scheme`：URL Scheme 前缀
- `description`：Scheme 描述
- `parameters`：可用参数列表
- `example`：使用示例

### 跨平台应用
- `app_name`：应用名称
- 各平台的包名/标识符
- `scheme`：URL Scheme 前缀
- `description`：Scheme 描述
- `parameters`：可用参数列表
- `example`：使用示例

## 使用方法

### 直接引用

可以直接在项目中引入 `url_schemes.json` 文件，使用各种编程语言的 JSON 解析功能读取数据：

```javascript
// JavaScript 示例
const fs = require('fs');
const urlSchemes = JSON.parse(fs.readFileSync('url_schemes.json', 'utf8'));

// 获取 iOS 平台的微信 URL Scheme
const wechatScheme = urlSchemes.ios.find(app => app.app_name === '微信');
console.log(wechatScheme.scheme); // 输出: weixin://
```

### 快捷指令集成

在 iOS/macOS 快捷指令中，可以使用这些 URL Scheme 创建深度链接操作，实现应用间的无缝跳转。

### 开发场景

在应用开发中，可以使用这些 URL Scheme 实现：
- 唤起其他应用
- 跳转到特定页面或功能
- 传递数据参数

## 应用场景

- **自动化工具**：创建工作流，自动跳转到指定应用的特定功能
- **快捷启动**：通过快捷方式快速访问应用内的特定页面
- **应用间协作**：实现不同应用之间的功能互通
- **测试与调试**：快速验证应用的 URL Scheme 响应

## 贡献指南

欢迎贡献更多应用的 URL Scheme！贡献步骤：

1. Fork 本仓库
2. 在 `url_schemes.json` 文件中添加新的应用信息
3. 确保数据格式正确，包含必要的字段
4. 提交 Pull Request

## 注意事项

- URL Scheme 可能随应用版本更新而变化
- 部分应用可能限制或更改其 URL Scheme 行为
- 使用前请确认目标设备上已安装对应应用
- 某些 URL Scheme 可能需要特定权限才能使用

## 许可证

本项目采用 MIT 许可证。详见 [LICENSE](LICENSE) 文件。
