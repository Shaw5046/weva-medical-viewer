# 📱 医疗记录二维码分享功能 - 使用指南

## 🎯 功能概述

此功能允许患者通过二维码分享自己的医疗记录给医生，医生扫码后可在浏览器中直接查看，无需登录或安装应用。

### 特点
- ✅ **完全免费** - 使用 GitHub Pages 托管，无服务器成本
- ✅ **无需后端** - 所有数据编码在URL中
- ✅ **即扫即看** - 医生扫码后立即在浏览器查看
- ✅ **隐私保护** - 数据不存储在任何服务器上
- ✅ **简单易用** - 一键生成二维码

---

## 📦 部署步骤

### 步骤 1: 部署 GitHub Pages

1. **创建 GitHub 仓库**
   ```bash
   # 在 GitHub 上创建新仓库: medical-viewer
   # 克隆到本地
   git clone https://github.com/YOUR_USERNAME/medical-viewer.git
   cd medical-viewer
   ```

2. **复制静态网页文件**
   ```bash
   # 复制项目中的 index.html
   cp /path/to/myweva/docs/github_pages/index.html .
   
   # 提交并推送
   git add index.html
   git commit -m "Add medical record viewer"
   git push origin main
   ```

3. **启用 GitHub Pages**
   - 进入仓库 Settings → Pages
   - Source 选择: `main` branch, `/root` folder
   - 点击 Save
   - 等待部署完成（约2-5分钟）

4. **获取 URL**
   ```
   https://YOUR_USERNAME.github.io/medical-viewer/
   ```

### 步骤 2: 配置 Flutter 应用

1. **更新 baseUrl**
   
   打开 `lib/utils/medical_share_generator.dart`：
   
   ```dart
   // 修改这一行，替换为您的 GitHub Pages URL
   static const String baseUrl = 'https://YOUR_USERNAME.github.io/medical-viewer';
   ```
   
   ⚠️ **重要**: 将 `YOUR_USERNAME` 替换为您的实际 GitHub 用户名！

2. **安装依赖**
   ```bash
   cd /path/to/myweva
   flutter pub get
   ```

3. **重新编译应用**
   ```bash
   flutter run
   # 或
   flutter build ios
   flutter build apk
   ```

---

## 🎮 使用方法

### 对于患者（Patient）

1. **打开应用，进入 Medical Record 主页**

2. **选择要分享的模块**
   - 在模块卡片上会看到两个按钮：
     - 🔵 **二维码图标** - 生成二维码（任何人可扫码查看）
     - 🔷 **分享图标** - 分享给特定用户（需要选择接收者）

3. **点击二维码图标**
   - 系统会自动加载该模块的数据
   - 生成二维码
   - 显示二维码对话框

4. **分享二维码**
   - **让医生扫码**: 直接展示二维码给医生扫描
   - **复制链接**: 点击 "Copy Link" 复制链接，通过微信/短信发送
   - **分享链接**: 点击 "Share Link" 通过系统分享功能发送

### 对于医生（Doctor）

1. **扫描二维码**
   - 使用微信扫一扫
   - 或使用系统相机扫描
   - 或任何支持扫描二维码的应用

2. **查看记录**
   - 扫码后自动在浏览器中打开
   - 显示患者的医疗记录
   - 可以滚动查看所有条目

3. **操作选项**
   - 截图保存
   - 打印页面（浏览器打印功能）
   - 分享链接给其他医生

---

## 📊 支持的模块

可以生成二维码分享的模块：

| 模块 | 支持 | 说明 |
|------|------|------|
| 📋 Diagnosis | ✅ | 诊断记录 |
| 🏥 Procedures | ✅ | 手术/治疗程序 |
| 💊 Medications | ✅ | 用药记录 |
| ⚠️ Allergies | ✅ | 过敏信息 |
| 💉 Vaccinations | ✅ | 疫苗接种记录 |
| ❤️ Biometrics | ✅ | 生物测量数据 |
| 🔍 Findings | ✅ | 症状/发现 |
| 📝 Medical Notes | ✅ | 医疗笔记 |
| 📁 My Uploads | ❌ | 文档上传（不支持）|

---

## ⚠️ 重要提示

### 数据大小限制

二维码有容量限制：
- **简单二维码**: 约 500 字符（容易扫描）
- **中等复杂**: 约 1000 字符
- **最大限制**: 约 2500 字符（较难扫描）

**建议**:
- 一次分享 5-10 条记录
- 如果记录太多，系统会提示"数据太大"
- 可以分批生成多个二维码

### 隐私与安全

⚠️ **重要提醒**:
- 二维码包含您的医疗信息
- 任何人扫描都可以查看
- 请只分享给信任的医疗人员
- 建议定期生成新的二维码

🔒 **安全特性**:
- 数据不存储在服务器上
- 通过 HTTPS 加密传输
- 没有追踪或分析脚本
- 纯静态页面，无后端

---

## 🛠️ 故障排除

### 1. 二维码生成失败

**错误**: "Data too large"

**原因**: 数据太大，超过二维码容量

**解决方案**:
- 减少分享的记录数量
- 分批生成多个二维码
- 只分享最重要的记录

---

### 2. 扫码后无法打开

**错误**: 页面显示 "No data found"

**原因**: URL不完整或损坏

**解决方案**:
- 确保二维码完整清晰
- 重新生成二维码
- 尝试复制链接直接发送

---

### 3. 页面显示 "Failed to decode data"

**错误**: 解码失败

**原因**: 数据格式错误或损坏

**解决方案**:
- 更新到最新版本应用
- 重新生成二维码
- 检查 GitHub Pages 是否正确部署

---

### 4. GitHub Pages 未部署

**错误**: 访问 URL 返回 404

**原因**: GitHub Pages 未启用或正在部署中

**解决方案**:
1. 检查仓库 Settings → Pages 是否已启用
2. 确认 `index.html` 在仓库根目录
3. 等待 5-10 分钟让 GitHub 完成部署
4. 检查浏览器控制台是否有错误

---

## 🎨 自定义样式

您可以修改 `index.html` 来自定义查看页面的外观：

### 修改颜色主题

```css
/* 主色调 */
.header {
    background: linear-gradient(135deg, #4C96D7 0%, #5A8FEC 100%);
}

/* 记录项边框颜色 */
.record-item {
    border-left: 4px solid #4C96D7;
}
```

### 修改字体

```css
body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}
```

### 修改布局宽度

```css
.container {
    max-width: 700px;  /* 修改为您想要的宽度 */
}
```

---

## 📱 测试流程

### 完整测试步骤

1. **部署测试**
   ```bash
   # 访问您的 GitHub Pages URL
   https://YOUR_USERNAME.github.io/medical-viewer/
   
   # 应该看到 "Loading medical records..." 然后显示错误
   # （因为还没有数据参数，这是正常的）
   ```

2. **应用测试**
   - 在应用中打开任意支持的模块（如 Diagnosis）
   - 点击模块卡片上的二维码图标
   - 等待数据加载
   - 查看生成的二维码

3. **扫码测试**
   - 使用微信"扫一扫"
   - 或使用手机相机扫描
   - 确认能在浏览器中正确显示数据

4. **功能测试**
   - 测试"复制链接"功能
   - 测试"分享链接"功能
   - 测试在不同浏览器中打开
   - 测试打印功能

---

## 🚀 性能优化

### 减少二维码复杂度

1. **只分享必要字段**
   - 在 `medical_share_generator.dart` 中移除不必要的字段
   
2. **压缩数据**
   - 已使用 gzip 压缩（约60%压缩率）
   
3. **使用短链接**（高级）
   - 可集成 bit.ly 或其他短链接服务
   - 将长URL转换为短URL

---

## 📞 技术支持

### 相关文件

- **Flutter 端**:
  - `lib/utils/medical_share_generator.dart` - 数据编码生成器
  - `lib/widgets/share/qr_share_dialog.dart` - 二维码显示对话框
  - `lib/screens/home/home_screen.dart` - 主页集成
  - `lib/widgets/home/module_card_grid.dart` - 模块卡片

- **Web 端**:
  - `docs/github_pages/index.html` - 查看页面
  - `docs/github_pages/README.md` - 部署说明

### 调试日志

应用会输出详细的调试日志：
```
🔵 [QR SHARE] Starting QR share for module: Diagnosis
📦 [SHARE GEN] Original data: 5 items
📦 [SHARE GEN] JSON size: 450 bytes
📦 [SHARE GEN] Compressed size: 280 bytes
📦 [SHARE GEN] Encoded length: 375 chars
📦 [SHARE GEN] Final URL length: 420 chars
```

在 Xcode Console 或 Android Logcat 中查看这些日志。

---

## ✅ 完成清单

在部署前检查：

- [ ] GitHub 仓库已创建
- [ ] `index.html` 已上传
- [ ] GitHub Pages 已启用
- [ ] 可以访问 GitHub Pages URL
- [ ] Flutter 代码中的 `baseUrl` 已更新
- [ ] `flutter pub get` 已运行
- [ ] 应用已重新编译
- [ ] 测试生成二维码成功
- [ ] 测试扫码查看成功

---

## 🎉 恭喜！

您已成功部署医疗记录二维码分享功能！

现在患者可以轻松地与医生分享医疗记录，医生只需扫码即可查看。

**祝使用愉快！** 🏥📱

