# 英汉词典 - 智能记单词网站

<div align="center">

📚 基于开源英汉词典数据的智能学习平台

[在线演示](https://tickurt.github.io/english-dictionary-web) | [快速开始](#快速开始) | [部署指南](DEPLOY.md) | [Docker 部署指南](docker_deploy.md)

</div>

## ✨ 功能特性

- 🔍 **强大搜索** - 快速搜索 25,000+ 英文单词
- 📖 **详细释义** - 双语释义、例句、词形变化、近义词对比
- 📚 **快速加入学习** - 单词详情页一键加入学习队列
- 🎵 **真人发音** - 免费 TTS 发音服务，支持多种语音
- 📝 **准确音标** - 免费在线音标服务，确保发音准确性
- 🔊 **自动朗读** - 智能自动朗读，支持个性化设置
- 📖 **句子朗读** - 例句一键朗读，提升学习体验
- 🧠 **科学记忆** - 基于 SM-2 算法的间隔重复记忆系统
- ☁️ **跨端同步** - 学习进度云端同步，随时随地学习
- ⚡ **智能缓存** - 本地优先，乐观更新，极速响应
- 📡 **离线支持** - 离线学习，恢复网络后自动同步
- ⭐ **收藏管理** - 收藏重要单词，随时复习
- 📊 **学习统计** - 可视化学习进度和成就
- ⌨️ **快捷键支持** - 键盘操作，提升学习效率
- 🌓 **深色模式** - 支持浅色/深色主题切换
- 📱 **响应式设计** - 完美适配手机、平板和电脑

## 🚀 技术栈

- **前端框架**: Vue 3 + Vite
- **状态管理**: Pinia
- **路由**: Vue Router
- **样式**: Tailwind CSS
- **数据存储**: Supabase (认证 + 数据库)
- **发音服务**: Web Speech API（浏览器原生）
- **音标服务**: Free Dictionary API + WordsAPI
- **词典数据**: [Open English Dictionary](https://github.com/ahpxex/open-english-dictionary)
- **部署**: GitHub Pages

## 📸 预览

![image](https://github.com/TICKurt/english-dictionary-web/blob/main/%E9%A6%96%E9%A1%B5.png)
![image](https://github.com/TICKurt/english-dictionary-web/blob/main/%E8%AF%8D%E5%85%B8%E6%A8%A1%E5%BC%8F.png)
![image](https://github.com/TICKurt/english-dictionary-web/blob/main/%E5%AD%A6%E4%B9%A0%E6%A8%A1%E5%BC%8F1.png)
![image](https://github.com/TICKurt/english-dictionary-web/blob/main/%E5%AD%A6%E4%B9%A0%E6%A8%A1%E5%BC%8F2.png)
![image](https://github.com/TICKurt/english-dictionary-web/blob/main/%E4%B8%AA%E4%BA%BA%E4%B8%AD%E5%BF%83.png)


## 🎯 快速开始

### 前置要求

- Node.js 18+
- npm 或 yarn

### 本地运行

1. **克隆仓库**

```bash
git clone https://github.com/TICKurt/english-dictionary-web.git
cd english-dictionary-web
```

2. **安装依赖**

```bash
npm install
```

3. **处理词典数据**

如果你已经将词典 JSON 文件放在 `public/dictionary/` 目录，运行：

```bash
npm run build-index
```

这将生成轻量级索引文件（约 3.4 MB），支持按需加载单词详情。

4. **配置环境变量**

创建 `.env` 文件（参考 `.env.example`）：

```env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

> 如何获取 Supabase 配置？查看 [部署指南](DEPLOY.md)

5. **启动开发服务器**

```bash
npm run dev
```

访问 http://localhost:5173

> 使用 Docker Compose 快速上线？参阅 [Docker 部署指南](docker_deploy.md)。

## 📦 构建

```bash
npm run build
```

构建产物将在 `dist/` 目录。

## 🎯 功能使用

### 发音功能

1. **学习模式**：点击单词旁边的 🔊 按钮即可播放发音
2. **单词详情**：在单词详情页面点击发音按钮
3. **快捷键**：支持键盘操作，提升学习效率
   - `空格键`：翻转单词卡片
   - `Esc键`：返回单词面
   - `1-3数字键`：快速评分掌握程度

### 学习模式

1. **开始学习**：进入学习模式，系统随机展示单词
2. **查看释义**：点击"查看释义"或按空格键翻转卡片
3. **评分掌握**：根据掌握程度选择 1-3 分
4. **收藏单词**：点击 ⭐ 收藏重要单词

## 🚢 部署

详细的部署指南请查看 [DEPLOY.md](DEPLOY.md)，包括：

1. 如何创建 Supabase 项目
2. 如何配置 GitHub Actions
3. 如何部署到 GitHub Pages
4. 常见问题解答

## 📊 项目结构

```
english-dictionary-web/
├── .github/
│   └── workflows/
│       └── deploy.yml          # GitHub Actions 自动部署
├── public/
│   └── dictionary/             # 词典数据（原始文件 + 索引）
├── src/
│   ├── assets/                 # 样式和资源
│   ├── components/             # Vue 组件
│   │   ├── WordCard.vue
│   │   ├── SearchBar.vue
│   │   ├── ProgressChart.vue
│   │   ├── SpeakerButton.vue   # 发音按钮组件
│   │   └── SentenceSpeaker.vue # 句子朗读组件
│   ├── views/                  # 页面视图
│   │   ├── Home.vue
│   │   ├── Study.vue
│   │   ├── Review.vue
│   │   ├── Collection.vue
│   │   ├── Profile.vue
│   │   ├── Settings.vue
│   │   ├── WordDetail.vue
│   │   └── Auth.vue
│   ├── stores/                 # Pinia 状态管理
│   │   ├── user.js
│   │   ├── dictionary.js
│   │   └── learning.js
│   ├── utils/                  # 工具函数
│   │   ├── supabase.js
│   │   ├── sm2.js
│   │   ├── dictionary.js
│   │   ├── tts.js              # 文本转语音工具
│   │   ├── phonetic.js         # 音标获取工具
│   │   └── settings.js         # 用户设置管理
│   ├── router/
│   │   └── index.js
│   ├── App.vue
│   └── main.js
├── scripts/
│   ├── build-index.js          # 构建轻量级索引脚本
│   └── process-dictionary.js   # 数据预处理脚本（已弃用）
├── supabase-schema.sql         # Supabase 数据库脚本
├── package.json
├── vite.config.js
├── tailwind.config.js
└── README.md
```

## 🧠 SM-2 记忆算法

本项目使用 SM-2（SuperMemo 2）算法来优化单词复习间隔：

- **质量评分**: 每次复习后评估记忆质量（0-5）
- **动态间隔**: 根据评分自动调整下次复习时间
- **难度因子**: 跟踪每个单词的学习难度
- **优化效率**: 在遗忘临界点前复习，提高记忆效率

## 🤝 贡献

欢迎贡献！请查看 [贡献指南](CONTRIBUTING.md)。

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开 Pull Request

## 🎵 发音功能

### 免费发音服务

本项目集成了多种免费的发音服务，确保用户能够听到准确的单词发音：

#### 技术方案

**Web Speech API（浏览器原生）**
- 浏览器内置，无需外部服务
- 高质量语音合成
- 免费使用，完全离线
- 支持多种语言和音色
- Edge、Chrome、Safari 均支持

#### 功能特性

- 🔊 **一键发音**：点击发音按钮即可播放
- 🎛️ **语速调节**：支持 0.1x - 2.0x 语速
- 🌍 **多语言支持**：支持英语、中文等多种语言
- ⏸️ **播放控制**：支持停止、重新播放
- 📱 **移动端优化**：完美适配手机和平板

#### 使用方法

```javascript
import { speakText, stopSpeaking } from '@/utils/tts'

// 播放单词发音
await speakText('hello', 'en', 1.0)

// 停止播放
stopSpeaking()
```

## 🔊 自动朗读功能

### 智能朗读系统

本项目集成了智能自动朗读系统，支持多种场景的自动朗读和个性化设置：

#### 功能特性

- 🎯 **场景化朗读**：支持单词详情、学习模式、搜索结果等不同场景
- ⚙️ **个性化设置**：可自定义朗读开关、语速、语言等参数
- 📱 **用户友好**：直观的设置界面，一键开启/关闭
- 🔄 **智能回退**：设置失败时自动使用默认配置

#### 朗读场景

1. **单词详情页**：进入单词详情时自动朗读单词
2. **学习模式**：学习新单词时自动朗读
3. **搜索结果**：搜索单词时自动朗读
4. **例句朗读**：点击例句旁的朗读按钮播放句子

#### 设置选项

- **自动朗读总开关**：控制是否启用自动朗读
- **场景开关**：分别控制不同场景的自动朗读
- **语速调节**：0.5x - 2.0x 语速范围
- **语言选择**：支持英语（美式/英式/澳式）、中文等

#### 使用方法

```javascript
import { autoSpeak, speakSentence } from '@/utils/tts'

// 自动朗读（根据设置决定是否朗读）
await autoSpeak('hello', 'wordDetail')

// 朗读句子
await speakSentence('Hello, how are you?')
```

## 📝 音标功能

### 免费音标服务

本项目集成了多种免费的在线音标服务，确保用户能够看到准确的音标：

#### 技术方案

1. **Free Dictionary API**（优先）
   - 完全免费，无需注册
   - 提供准确的 IPA 音标
   - 支持多种发音变体

2. **WordsAPI (RapidAPI)**（备选）
   - 高质量音标数据
   - 需要免费注册获取 API Key
   - 支持批量查询

#### 功能特性

- 📝 **自动获取**：查看单词时自动获取最新音标
- 🔄 **智能回退**：在线服务失败时使用原始数据
- ⚡ **缓存优化**：音标结果本地缓存，避免重复请求
- 🎯 **准确可靠**：优先使用权威在线服务，确保准确性
- 📱 **加载提示**：显示音标获取进度，提升用户体验

#### 使用方法

```javascript
import { getPhonetic, getBatchPhonetics } from '@/utils/phonetic'

// 获取单个单词音标
const phonetic = await getPhonetic('hello', '/həˈloʊ/')

// 批量获取音标
const words = [
  { word: 'hello', phonetic: '/həˈloʊ/' },
  { word: 'world', phonetic: '/wɜːrld/' }
]
const results = await getBatchPhonetics(words)
```

## ⚡ 性能优化

### 按需加载 + 智能缓存

本项目采用按需加载策略，极大提升了性能和用户体验：

#### 核心优化

1. **轻量级索引**：首次只加载 3.4MB 索引文件
2. **按需加载**：查看单词时才下载详情（2-5KB）
3. **三层缓存**：内存 + IndexedDB + HTTP 缓存
4. **乐观更新**：用户操作立即生效，后台同步

#### 性能提升

| 场景 | 旧方案 | 新方案 | 提升 |
|-----|--------|--------|------|
| 查看 10 个单词 | 10-30MB | 3.43MB | **节省 65%+** |
| 搜索单词 | 1-3秒 | 即时 | **100%** |
| 缓存响应 | 300ms | <10ms | **30倍** |

详细说明请查看 [CACHING.md](CACHING.md)

## 📝 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🙏 致谢

- [Open English Dictionary](https://github.com/ahpxex/open-english-dictionary) - 提供高质量的词典数据
- [Supabase](https://supabase.com/) - 提供免费的后端服务
- [Vue.js](https://vuejs.org/) - 优秀的前端框架
- [Tailwind CSS](https://tailwindcss.com/) - 实用的 CSS 框架
- [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API) - 浏览器原生语音合成服务
- [Free Dictionary API](https://dictionaryapi.dev/) - 免费音标和发音服务
- [WordsAPI](https://rapidapi.com/dpventures/api/wordsapi) - 高质量词典和音标数据

## 📮 联系方式

如有问题或建议，欢迎：

- 提交 [Issue](https://github.com/TICKurt/english-dictionary-web/issues)

---

⭐ 如果这个项目对你有帮助，请给它一个 Star！
