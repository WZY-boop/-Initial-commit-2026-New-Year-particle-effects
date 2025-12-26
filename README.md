# 🎆 2026 新年快乐 - 粒子交互特效

<div align="center">

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Canvas](https://img.shields.io/badge/Canvas-FF6B6B?style=for-the-badge&logo=html5&logoColor=white)

一个基于 Canvas 的新年祝福特效页面，包含粒子物理交互、烟花动画和星空背景

[在线演示](#) | [功能特性](#-功能特性) | [快速开始](#-快速开始)

</div>

---

## ✨ 功能特性

### 🎨 视觉效果
- **粒子文字系统** - 文字由数千个粒子组成，支持渐变色
- **烟花特效** - 随机发射的烟花，带有重力和拖尾效果
- **星空背景** - 闪烁的星星营造浪漫氛围
- **流光拖尾** - 粒子移动时产生长曝光效果

### 🖱️ 交互功能
- **鼠标斥力场** - 鼠标靠近时粒子会被推开
- **触摸支持** - 完美适配移动端触摸操作
- **自动播放** - 文字自动切换，展示新年祝福

### ⚡ 性能优化
- **自适应渲染** - 根据设备性能自动调整粒子密度
- **移动端优化** - 针对手机屏幕优化粒子数量和大小
- **智能复用** - 粒子对象复用，减少内存开销

---

## 🎬 效果预览

### 桌面端
- 分辨率：1920x1080 及以上
- 粒子数量：约 3000-5000 个
- 交互方式：鼠标移动

### 移动端
- 自动适配屏幕尺寸
- 粒子数量：约 1000-2000 个
- 交互方式：触摸滑动

---

## 🚀 快速开始

### 方法一：直接打开
```bash
# 克隆仓库
git clone https://github.com/WZY-boop/-Initial-commit-2026-New-Year-particle-effects.git

# 进入目录
cd 2026-newyear

# 用浏览器打开 index.html
```

### 方法二：本地服务器
```bash
# 使用 Python 启动服务器
python -m http.server 8000

# 或使用 Node.js
npx serve

# 访问 http://localhost:8000
```

### 方法三：在线部署
支持部署到以下平台：
- GitHub Pages
- Vercel
- Netlify
- Cloudflare Pages

---

## 📁 项目结构

```
2026-newyear/
│
├── index.html          # 主页面（包含所有代码）
└── README.md          # 项目说明文档
```

---

## 🎯 核心技术

### 1. 粒子物理引擎
```javascript
// 鼠标斥力场算法
let distance = Math.sqrt(dx * dx + dy * dy);
let force = (maxDistance - distance) / maxDistance;
```
- 计算粒子与鼠标的距离
- 根据距离计算斥力大小
- 粒子被推开后缓慢回到原位

### 2. 流光拖尾效果
```javascript
ctx.fillStyle = 'rgba(0, 0, 0, 0.15)';
ctx.globalCompositeOperation = 'lighter';
```
- 使用半透明黑色覆盖画布
- 启用 `lighter` 混合模式
- 产生霓虹发光效果

### 3. 文字渐变采样
```javascript
const gradient = offCtx.createLinearGradient(0, 0, width, 0);
gradient.addColorStop(0, '#ff3333');
gradient.addColorStop(0.5, '#ffd700');
```
- 在离屏 Canvas 绘制渐变文字
- 逐像素采样获取颜色
- 每个粒子保留原始 RGB 值

---

## 🎨 自定义配置

### 修改文字内容
编辑 `TEXT_LIST` 数组：
```javascript
const TEXT_LIST = [
    "✨", "再见 2025", "3", "2", "1",
    "2026", "新年快乐", "万事胜意", "平安喜乐", "❤️"
];
```

### 调整粒子密度
```javascript
const PARTICLE_GAP = IS_MOBILE ? 6 : 4; // 数值越大，粒子越少
```

### 修改鼠标交互范围
```javascript
const MOUSE_RADIUS = 120; // 像素单位
```

### 更换背景音乐
```html
<audio id="bg-music" loop>
    <source src="你的音乐文件.mp3" type="audio/mpeg">
</audio>
```

---

## 🌐 浏览器兼容性

| 浏览器 | 版本要求 | 支持情况 |
|--------|---------|---------|
| Chrome | 60+ | ✅ 完美支持 |
| Firefox | 55+ | ✅ 完美支持 |
| Safari | 11+ | ✅ 完美支持 |
| Edge | 79+ | ✅ 完美支持 |
| IE | - | ❌ 不支持 |

---

## 📱 移动端适配

- ✅ 响应式设计，自动适配屏幕尺寸
- ✅ 触摸事件支持
- ✅ 禁止下拉刷新 (`touch-action: none`)
- ✅ 性能优化，减少粒子数量
- ✅ 字体大小自动调整

---

## ⚙️ 性能优化建议

### 低端设备优化
```javascript
// 进一步降低粒子密度
const PARTICLE_GAP = IS_MOBILE ? 8 : 6;

// 减少星星数量
const count = IS_MOBILE ? 30 : 100;

// 降低烟花频率
if (Math.random() < 0.02) fireworks.push(new Firework());
```

### 高端设备增强
```javascript
// 增加粒子密度
const PARTICLE_GAP = IS_MOBILE ? 4 : 2;

// 增加烟花粒子
const count = IS_MOBILE ? 80 : 150;
```

---

## 🐛 常见问题

### Q: 音乐无法播放？
**A:** 现代浏览器需要用户交互才能播放音频，请点击"开启新年之旅"按钮。如果仍无法播放，请检查音频文件路径或使用本地音频文件。

### Q: 页面卡顿怎么办？
**A:** 尝试以下方法：
1. 增大 `PARTICLE_GAP` 值（减少粒子数量）
2. 降低烟花生成频率
3. 减少星星数量

### Q: 移动端触摸无反应？
**A:** 确保浏览器支持触摸事件，并且没有被其他元素遮挡。

### Q: 如何部署到 GitHub Pages？
**A:** 
```bash
# 1. 创建 gh-pages 分支
git checkout -b gh-pages

# 2. 推送到 GitHub
git push origin gh-pages

# 3. 在仓库设置中启用 GitHub Pages
```

---

## 🎓 技术亮点

1. **纯原生实现** - 无需任何第三方库
2. **物理引擎** - 粒子具有密度、缓动等物理属性
3. **智能复用** - 文字切换时粒子对象复用
4. **性能监控** - 自动检测设备性能并调整参数
5. **优雅降级** - 低端设备自动降低特效质量

---

## 📄 开源协议

本项目采用 [MIT License](LICENSE) 开源协议

---

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 提交 Pull Request

---

## 💖 致谢

- 灵感来源：Canvas 粒子动画
- 音乐来源：网易云音乐
- 字体：Microsoft YaHei

---

## 📧 联系方式

如有问题或建议，欢迎联系：

- GitHub Issues: [提交问题](https://github.com/WZY-boop)

---

<div align="center">

**⭐ 如果这个项目对你有帮助，请给个 Star 吧！⭐**

Made with ❤️ by [WZY-boop]

</div>


