# URL Schemes Collection

一个精选的热门应用和系统 URL Scheme 集合，以 JSON 格式存储。便于查询和集成应用专属深度链接，适用于自动化、快捷指令或开发场景。

## 文件结构

项目文件已按以下方式组织：

- **ios_schemes.json** - 包含 iOS 系统相关的 URL Schemes（设置、日历、地图等系统应用）
- **android_schemes.json** - 包含 Android 系统相关的 URL Schemes（设置、拨号、短信等系统应用）
- **common_schemes.json** - 包含跨平台常见应用的 URL Schemes（微信、QQ、支付宝、微博、知乎、美团、滴滴打车等）

## 功能特点

- **系统应用支持**：分别收录 iOS 和 Android 系统原生应用的 URL Schemes
- **常见应用覆盖**：包含社交、电商、出行、工具等各类热门应用
- **详细参数**：提供每个 URL Scheme 的参数说明和使用示例
- **结构化数据**：采用清晰的 JSON 格式，便于程序解析和使用
- **分类明确**：按系统和应用类型进行合理分类

## 数据结构

### 系统应用文件（ios_schemes.json, android_schemes.json）
- 根节点为 `ios_system` 或 `android_system` 数组
- 每个应用包含以下字段：
  - `app_name`：应用名称
  - `bundle_id`/`package_name`：应用包名
  - `scheme`：URL Scheme 前缀
  - `description`：Scheme 描述
  - `parameters`：可用参数列表
  - `example`：使用示例

### 常见应用文件（common_schemes.json）
- 根节点为 `common_apps` 数组
- 每个应用包含以下字段：
  - `app_name`：应用名称
  - `ios_bundle_id`：iOS 平台包名
  - `android_package_name`：Android 平台包名
  - `scheme`：URL Scheme 前缀
  - `description`：Scheme 描述
  - `parameters`：可用参数列表
  - `example`：使用示例

## 使用方法

### 直接引用

可以直接在项目中引入相应的 JSON 文件，使用各种编程语言的 JSON 解析功能读取数据：

```javascript
// JavaScript 示例：获取 iOS 设置应用的 URL Scheme
const fs = require('fs');
const iosSchemes = JSON.parse(fs.readFileSync('ios_schemes.json', 'utf8'));
const settingsScheme = iosSchemes.ios_system.find(app => app.app_name === '设置');
console.log(settingsScheme.scheme); // 输出: prefs://

// 获取常用应用的 URL Scheme
const commonSchemes = JSON.parse(fs.readFileSync('common_schemes.json', 'utf8'));
const wechatScheme = commonSchemes.common_apps.find(app => app.app_name === '微信');
console.log(wechatScheme.scheme); // 输出: weixin://
```

### 获取特定参数

```javascript
// 获取微信可用的所有参数
const wechatParams = wechatScheme.parameters;
wechatParams.forEach(param => {
  console.log(`${param.param}: ${param.description}`);
});
```

### 快捷指令集成

在 iOS 快捷指令中，可以使用 `ios_schemes.json` 和 `common_schemes.json` 中的 URL Scheme 创建深度链接操作，实现应用间的无缝跳转：

1. 在快捷指令中添加「打开 URL」操作
2. 输入相应的 URL Scheme，如 `prefs://Bluetooth` 或 `weixin://dl/scan`
3. 可以通过变量动态构建参数，实现更灵活的操作

### 开发场景

在应用开发中，可以根据不同需求使用相应的 URL Scheme 文件：

- **系统集成**：使用系统应用的 URL Scheme 进行系统级功能调用
- **应用间通信**：使用常见应用的 URL Scheme 实现跨应用交互
- **自动化测试**：快速验证应用的 URL Scheme 响应和功能

## 应用场景

- **自动化工具**：创建工作流，自动跳转到指定应用的特定功能
- **快捷启动**：通过快捷方式快速访问应用内的特定页面
- **应用间协作**：实现不同应用之间的功能互通
- **测试与调试**：快速验证应用的 URL Scheme 响应
- **系统管理**：快速访问系统设置和功能

## 贡献指南

欢迎贡献更多应用的 URL Scheme！贡献步骤：

1. Fork 本仓库
2. 根据应用类型，在相应的文件中添加新的应用信息：
   - iOS 系统应用 -> `ios_schemes.json`
   - Android 系统应用 -> `android_schemes.json`
   - 常见跨平台应用 -> `common_schemes.json`
3. 确保数据格式正确，包含所有必要的字段
4. 提交 Pull Request

## 注意事项

- URL Scheme 可能随应用版本更新而变化
- 部分应用可能限制或更改其 URL Scheme 行为
- 使用前请确认目标设备上已安装对应应用
- 某些 URL Scheme 可能需要特定权限才能使用
- 系统应用的 URL Scheme 可能因系统版本不同而有所差异

## 许可证

本项目采用 MIT 许可证。详见 [LICENSE](LICENSE) 文件。
