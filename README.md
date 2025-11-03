# Medical Record Viewer - GitHub Pages Setup

这个静态网页用于显示通过QR码分享的医疗记录。

## 📦 部署到 GitHub Pages

### 步骤 1: 创建 GitHub 仓库

1. 在 GitHub 上创建一个新仓库，命名为 `medical-viewer`
2. 仓库可以是 Public 或 Private（如果您有 GitHub Pro）

### 步骤 2: 上传文件

1. 将 `index.html` 文件上传到仓库根目录
2. 或者克隆仓库并提交文件：

```bash
git clone https://github.com/YOUR_USERNAME/medical-viewer.git
cd medical-viewer
# 复制 index.html 到这里
git add index.html
git commit -m "Add medical record viewer"
git push origin main
```

### 步骤 3: 启用 GitHub Pages

1. 进入仓库的 Settings
2. 在左侧菜单找到 "Pages"
3. 在 "Source" 部分，选择：
   - Branch: `main`
   - Folder: `/root` 或 `/docs`（如果您将文件放在 docs 文件夹）
4. 点击 "Save"
5. 等待几分钟，GitHub 会自动部署

### 步骤 4: 获取 URL

部署成功后，您的网页将可通过以下URL访问：

```
https://YOUR_USERNAME.github.io/medical-viewer/
```

### 步骤 5: 更新 Flutter 代码

在 `lib/utils/medical_share_generator.dart` 中更新 `baseUrl`：

```dart
static const String baseUrl = 'https://YOUR_USERNAME.github.io/medical-viewer';
```

**重要提示**: 将 `YOUR_USERNAME` 替换为您的实际 GitHub 用户名！

## 🧪 测试

1. 在 Flutter 应用中生成一个 QR 码
2. 使用微信或相机扫描 QR 码
3. 确认能在浏览器中正确显示医疗记录

## 📝 自定义

您可以修改 `index.html` 中的样式来自定义外观：

- **颜色主题**: 修改 CSS 中的颜色值（如 `#4C96D7`）
- **字体**: 修改 `font-family`
- **布局**: 调整 `.container` 的 `max-width`

## 🔒 隐私说明

- 所有数据都编码在 URL 中，不存储在服务器上
- 页面是纯静态的，没有后端
- 没有分析或跟踪脚本
- 建议使用 HTTPS（GitHub Pages 默认提供）

## ⚡ 性能优化

如果QR码太复杂（数据太大）：

1. 减少分享的记录数量
2. 移除不必要的字段（如 details, subtitle）
3. 考虑使用短链接服务

## 🛠️ 故障排除

### QR码扫描后显示错误

- **原因**: URL 可能太长或数据格式错误
- **解决**: 减少分享的记录数量

### 页面显示 "No data found"

- **原因**: URL 中没有 `#/view?d=` 参数
- **解决**: 确保完整扫描 QR 码

### 页面加载失败

- **原因**: GitHub Pages 可能还在部署中
- **解决**: 等待 5-10 分钟后重试

## 📱 支持的浏览器

- ✅ Chrome / Edge (推荐)
- ✅ Safari
- ✅ Firefox
- ✅ 微信内置浏览器
- ✅ 移动端浏览器

## 🔄 更新

当您需要更新页面时：

1. 修改 `index.html`
2. 提交并推送到 GitHub
3. GitHub Pages 会自动重新部署（通常需要 1-2 分钟）

---

**完成！现在您可以通过 QR 码分享医疗记录了！** 🎉

