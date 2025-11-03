# 🚀 快速开始 - 5分钟部署指南

## ⚡ 最简部署流程

### 1️⃣ 创建 GitHub 仓库 (2分钟)

```bash
# 方法1: 通过 GitHub 网页
1. 访问 https://github.com/new
2. 仓库名: medical-viewer
3. 选择 Public
4. 点击 "Create repository"

# 方法2: 通过命令行（如果已安装 gh CLI）
gh repo create medical-viewer --public
```

### 2️⃣ 上传 index.html (1分钟)

**方法 A: 直接在 GitHub 网页上传**
1. 进入刚创建的仓库
2. 点击 "Add file" → "Upload files"
3. 拖拽 `docs/github_pages/index.html` 文件
4. 点击 "Commit changes"

**方法 B: 使用 Git 命令**
```bash
git clone https://github.com/YOUR_USERNAME/medical-viewer.git
cd medical-viewer
cp /path/to/myweva/docs/github_pages/index.html .
git add index.html
git commit -m "Add medical viewer"
git push
```

### 3️⃣ 启用 GitHub Pages (1分钟)

1. 进入仓库 → Settings → Pages
2. Source: 选择 `main` 分支
3. 点击 Save
4. 等待 2-5 分钟

✅ 完成！您的页面地址：
```
https://YOUR_USERNAME.github.io/medical-viewer/
```

### 4️⃣ 更新 Flutter 代码 (1分钟)

打开 `lib/utils/medical_share_generator.dart`：

```dart
// 第6行，修改这里：
static const String baseUrl = 'https://YOUR_USERNAME.github.io/medical-viewer';
//                                    ^^^^^^^^^^^^^^^^
//                             替换成您的 GitHub 用户名
```

保存后运行：
```bash
flutter pub get
flutter run
```

---

## ✅ 测试

1. **在应用中**：
   - 进入 Medical Record
   - 点击任意模块的二维码图标 🔵
   - 等待生成二维码

2. **扫码测试**：
   - 用微信扫一扫
   - 确认能在浏览器打开并显示数据

---

## ❓ 常见问题

### Q: GitHub Pages 显示 404

**A**: 等待 5-10 分钟，GitHub 需要时间部署。检查 Settings → Pages 是否显示绿色勾选。

### Q: 应用报错 "Data too large"

**A**: 一次分享的记录太多了。减少记录数量，或分批生成多个二维码。

### Q: 扫码后显示 "No data found"

**A**: 确保：
1. Flutter 代码中的 `baseUrl` 已更新
2. 应用已重新编译
3. 二维码完整清晰

---

## 📚 完整文档

详细说明请查看：
- 📖 [完整使用指南](../QR_SHARE_GUIDE.md)
- 🛠️ [GitHub Pages 部署说明](README.md)

---

**🎉 恭喜！5分钟完成部署！现在就可以开始使用了！**

