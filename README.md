# Bilibili 视频过滤器

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/StarsWhere/Bilibili-Video-Filter/blob/main/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/StarsWhere/Bilibili-Video-Filter.svg?style=social&label=Star)](https://github.com/StarsWhere/Bilibili-Video-Filter)
[![GitHub forks](https://img.shields.io/github/forks/StarsWhere/Bilibili-Video-Filter.svg?style=social&label=Fork)](https://github.com/StarsWhere/Bilibili-Video-Filter)

B站推荐过滤器是一个用户脚本（UserScript），专为 Bilibili（哔哩哔哩）首页设计。它可以智能屏蔽广告、特定分类、直播推荐以及自定义关键词，帮助用户获得更干净、个性化的浏览体验。脚本支持自适应持续屏蔽、拖拽控制面板、暗黑模式切换，并修复了屏蔽后页面留白问题，优化了 UI 交互。

## 功能特性

- **广告屏蔽**：自动移除首页的广告卡片和推广内容。
- **分类屏蔽**：屏蔽指定分类（如番剧、直播、国创等），可自定义黑名单。
- **直播推荐屏蔽**：隐藏直播卡片和正在直播标记。
- **视频关键词屏蔽**：根据视频标题或 UP 主名称过滤自定义关键词。
- **自适应持续屏蔽**：动态调整屏蔽间隔，根据屏蔽数量优化性能，避免卡顿。
- **拖拽控制面板**：浮动按钮可拖动位置，点击打开管理面板。
- **暗黑模式支持**：一键切换主题，适应夜间浏览。
- **状态指示器**：实时显示已屏蔽项目数量。
- **修复页面留白**：屏蔽后自动优化布局，避免空白区域。
- **持久化配置**：使用 Tampermonkey 的存储功能，设置自动保存。

脚本版本：**7.0.0**  
作者：**StarsWhere**  
许可证：**MIT**

## 安装指南

1. **安装 Tampermonkey**：
   - 在 Chrome/Firefox/Edge 等浏览器中安装 [Tampermonkey 扩展](https://www.tampermonkey.net/)。
   - 如果使用其他用户脚本管理器（如 Violentmonkey），也可兼容。

2. **安装脚本**：
   - 访问 [GitHub 仓库](https://github.com/StarsWhere/Bilibili-Video-Filter)。
   - 点击 `Bilibili-Video-Filter.js` 文件，浏览器会提示安装脚本。
   - 或者，从 Tampermonkey 仪表盘点击“从 URL 安装”，输入脚本的 raw URL：  
     `https://raw.githubusercontent.com/StarsWhere/Bilibili-Video-Filter/main/Bilibili-Video-Filter.js`

3. **启用脚本**：
   - 安装后，Tampermonkey 会自动启用脚本。
   - 访问 Bilibili 首页（`https://www.bilibili.com/`），脚本将立即生效（排除视频播放页面）。

**注意**：脚本匹配规则为 `*://www.bilibili.com/*`，但排除视频页面 `*://www.bilibili.com/video/*`，以避免干扰正常观看。

## 使用方法

### 控制面板
- 在 Bilibili 首页右下角会出现一个浮动按钮（🛡️），可拖拽到任意位置。
- 点击按钮打开主控制面板：
  - **开关选项**：启用/禁用广告、直播、分类和视频关键词屏蔽。
  - **自适应持续屏蔽**：开启后，脚本会持续监控页面变化，智能调整屏蔽频率。
  - **管理黑名单**：点击“管理”按钮打开子面板，添加/删除关键词或分类。
  - **立即执行**：手动触发一次屏蔽扫描。
  - **重置配置**：清除所有设置并刷新页面。
  - **主题切换**：在面板右上角切换暗黑/浅色模式。
- 点击页面空白处或关闭按钮可隐藏面板。

### 配置自定义屏蔽
- **视频关键词**：在“视频关键词屏蔽”管理面板中输入标题或 UP 主名（如“广告”或“某UP主”），回车或点击“添加”保存。脚本会过滤包含这些词的视频卡片。
- **分类屏蔽**：默认屏蔽番剧、直播、国创等常见分类。可在管理面板自定义添加（如“电影”）。
- 配置会自动保存，下次访问生效。

### 示例截图
（由于这是文本 README，您可以在仓库中查看实际截图或自行安装体验。）

- 主控制面板：显示开关和快速操作。
- 管理面板：列表形式管理黑名单，支持删除。
- 浮动按钮：拖拽式 UI，简洁美观。
- 屏蔽效果：首页干净无广告，布局紧凑无留白。

## 性能优化
- **节流与防抖**：使用 debounce 和 throttle 避免频繁 DOM 操作。
- **自适应间隔**：屏蔽活跃时缩短间隔（最小 500ms），闲置时延长（最大 8000ms）。
- **MutationObserver**：监控页面动态变化，仅在必要时执行屏蔽。
- **兼容性**：测试于 Chrome 100+、Firefox 90+，支持移动端触摸拖拽。

## 常见问题
- **脚本未生效？** 检查 Tampermonkey 是否启用，并确保访问 Bilibili 首页（非视频页）。
- **页面卡顿？** 关闭“自适应持续屏蔽”或调整浏览器扩展。
- **黑名单不生效？** 确保关键词精确匹配（区分大小写），或刷新页面。
- **暗黑模式失效？** 脚本仅修改面板样式，Bilibili 官方主题需单独设置。

如果遇到 bug，请在 [GitHub Issues](https://github.com/StarsWhere/Bilibili-Video-Filter/issues) 提交反馈。

## 贡献
欢迎贡献！  
1. Fork 仓库。
2. 创建分支（如 `feature/new-filter`）。
3. 提交 PR，描述变更。
4. 遵守代码风格（ES6+，注释清晰）。

## 许可证
本项目采用 [MIT 许可证](https://github.com/StarsWhere/Bilibili-Video-Filter/blob/main/LICENSE)。  
Copyright (c) 2023 StarsWhere。

---

感谢使用！如果脚本提升了您的 Bilibili 体验，欢迎点亮 GitHub Star ⭐ 支持项目。
