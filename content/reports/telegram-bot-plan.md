---
title: "小型 Telegram Bot 项目规划"
date: 2026-03-01
description: "使用 Hugo 搭建 Telegram Bot 项目的完整指南"
tags: ["Telegram", "Bot", "Node.js"]
categories: ["指南"]
---

# 🤖 小型 Telegram Bot 项目规划

## 一、框架比较 (2026 最新)

| 框架 | 版本 | 描述 | 适合对象 |
|------|------|------|----------|
| **Telegraf** | 4.16.3 | Modern Telegram Bot Framework | 中级~高级 |
| **grammy** | 1.40.1 | The Telegram Bot Framework | 初学者~中级 |
| **node-telegram-bot-api** | 0.67.0 | 简单直接的 API 封装 | 初学者 |

### 详细比较

#### 🥇 **Telegraf** (推荐)
- **优点**: 功能最齐全、Middleware 系统强大、TypeScript 支持好、社区庞大
- **缺点**: 学习曲线较陡
- **适合**: 需要复杂功能的 Bot

#### 🥈 **grammy**
- **优点**: 官方维护、文档最完善、类型安全、插件生态丰富
- **缺点**: 相对新颖，较少历史包袱
- **适合**: 初学者想要好文档

#### 🥉 **node-telegram-bot-api**
- **优点**: 简单直观、极易上手
- **缺点**: 较少高级功能
- **适合**: 快速原型、简单 Bot

---

## 二、推荐项目结构

```
my-telegram-bot/
├── src/
│   ├── index.ts          # 入口文件
│   ├── commands/         # 指令处理
│   │   ├── start.ts
│   │   └── help.ts
│   ├── handlers/         # 消息处理
│   │   └── echo.ts
│   ├── keyboards/        # 自定义键盘
│   │   └── main.ts
│   ├── middlewares/      # 中间件
│   │   └── log.ts
│   ├── services/         # 业务逻辑
│   │   └── weather.ts
│   └── types/            # 类型定义
│       └── index.ts
├── .env                  # 环境变量
├── package.json
└── tsconfig.json
```

---

## 三、初学者代码 (使用 Telegraf)

### 1. 安装依赖
```bash
npm init -y
npm install telegraf dotenv
npm install -D typescript @types/node tsx
```

### 2. 环境变量 (.env)
```
TELEGRAM_BOT_TOKEN=你的BotToken
```

### 3. 基础代码 (src/index.ts)
```typescript
import { Telegraf, Markup, Keyboard } from 'telegraf';
import 'dotenv/config';

const bot = new Telegraf(process.env.TELEGRAM_BOT_TOKEN!);

// 🟢 /start 指令
bot.command('start', async (ctx) => {
  const welcomeText = `
👋 欢迎来到我的 Bot！

我是你的个人助理，请选择功能：
  `;
  
  const keyboard = Markup.keyboard([
    ['📝 发送消息', '🎮 玩游戏'],
    ['🌤️ 天气查询', '⚙️ 设置'],
    ['❓ 帮助']
  ]).resize();
  
  await ctx.reply(welcomeText, keyboard);
});

// 🟢 /help 指令
bot.command('help', async (ctx) => {
  await ctx.reply(`
📖 可用指令：
/start - 开始使用
/help - 显示帮助
/settings - 设置
  `);
});

// 🟢 按钮回复
bot.hears('📝 发送消息', async (ctx) => {
  await ctx.reply('请输入你想发送的消息：');
});

// 🟢 监听文字消息
bot.on('text', async (ctx) => {
  const message = ctx.message.text;
  
  // 简单的回复逻辑
  if (message.includes('你好')) {
    await ctx.reply('你好！👋');
  } else if (message.includes('天气')) {
    await ctx.reply('请使用 🌤️ 天气查询 按钮来查询天气');
  } else {
    // Echo 回复
    await ctx.reply(`你说的是：${message}`);
  }
});

// 🟢 错误处理
bot.catch((err, ctx) => {
  console.error('Bot 错误:', err);
  ctx.reply('抱歉，发生错误了！');
});

// 🔵 启动 Bot
bot.launch().then(() => {
  console.log('🤖 Bot 已启动！');
});

// 优雅关闭
process.once('SIGINT', () => {
  bot.stop('SIGINT');
  console.log('Bot 已关闭');
});
```

---

## 四、UI/UX 设计建议

### 🎨 视觉原则
1. **使用表情符号** - Telegram 原生支持，让按钮更直观
2. **按钮优先** - 减少用户打字，提供快速回复按钮
3. **富文本** - 适当使用粗体、斜体、代码块
4. **Loading 状态** - 长时间操作显示 "typing..."

### 📱 键盘示例
```typescript
// 内联按钮 (Inline Keyboard)
Markup.inlineKeyboard([
  [Markup.button.callback('✅ 确认', 'confirm')],
  [Markup.button.callback('❌ 取消', 'cancel')]
])

// 自定义键盘
Markup.keyboard([
  ['📝 发送', '📋 复制'],
  ['🔙 返回']
]).resize()
```

### 💡 UX 小技巧
- 首次互动显示引导
- 支持 /指令 快速操作
- 错误消息要友好
- 支持回复/引用消息

---

## 五、推广建议

### 🌐 发布平台
1. **Telegram Bot Store** - 搜索 "Telegram bot directory"
2. **GitHub** - 开源并加入 topic: telegram-bot
3. **Reddit** - r/telegram、r/bots
4. **Product Hunt** - 发布你的 Bot

### 📣 宣传策略
1. **功能演示视频** - 展示核心功能
2. **使用截图** - 漂亮的 UI 截图
3. **邀请链接** - t.me/yourbot?start=ref
4. **社群分享** - 相关 Telegram 群组

### 🔄 持续优化
- 收集用户反馈
- A/B 测试不同回复文案
- 分析 Bot 数据 (使用 botanalytics.co)
- 定期更新功能

---

## 六、下一步

1. **申请 Bot Token**: @BotFather
2. **建立项目**: 复制上面的结构
3. **本地测试**: 使用 ngrok 测试 Webhook
4. **部署上线**: Vercel / Railway / Fly.io

需要我帮你写更具体的功能代码吗？
