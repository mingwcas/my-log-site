---
title: "语音转文字工具安装指南"
date: 2026-03-01
description: "macOS 环境下语音转文字工具安装指南"
tags: ["语音识别", "STT", "macOS"]
categories: ["指南"]
---

# 🎤 语音转文字工具安装指南

> 适用于 macOS 环境

---

## 方案一：faster-whisper（推荐 ✅）

这是你已经安装的套件，只需要修复网络问题即可使用。

### 问题诊断
```
ImportError: Using SOCKS proxy, but the 'socksio' package is not installed
```

### 解决方案

```bash
# 方法1：安装 socksio
pip3 install socksio

# 方法2：或安装完整的 httpx
pip3 install "httpx[socks]"
```

### 然后下载模型
```bash
# 首次运行会自动下载模型（需要代理访问 HuggingFace）
# 设置代理
export HTTP_PROXY=http://127.0.0.1:7890
export HTTPS_PROXY=http://127.0.0.1:7890

# 运行转录
python3 -c "
from faster_whisper import WhisperModel
model = WhisperModel('tiny', device='cpu', compute_type='int8')
segments, info = model.transcribe('/tmp/audio.wav', language='zh')
for segment in segments:
    print(segment.text)
"
```

### 模型大小选择
| 模型 | 大小 | 速度 | 准确度 |
|------|------|------|--------|
| tiny | ~75 MB | 最快 | 较低 |
| base | ~150 MB | 快 | 中等 |
| small | ~500 MB | 中等 | 较高 |
| medium | ~1.5 GB | 慢 | 高 |
| large | ~3 GB | 最慢 | 最高 |

**初学者推荐**：tiny 或 base

---

## 方案二：OpenAI Whisper CLI

```bash
# 安装
pip3 install openai-whisper

# 转录
whisper /tmp/audio.wav --language Chinese --model tiny
```

---

## 方案三：Vosk（轻量级）

```bash
# 安装
pip3 install vosk

# 下载模型（中文）
# https://alphacephei.com/vosk/models

# 使用
python3 << 'EOF'
from vosk import Model, KaldiRecognizer
import wave
import json

model = Model("vosk-model-cn-0.15")
rec = KaldiRecognizer(model, 16000)

with wave.open("/tmp/audio.wav", "rb") as wf:
    while True:
        data = wf.readframes(4000)
        if len(data) == 0:
            break
        rec.AcceptWaveform(data)

result = json.loads(rec.FinalResult())
print(result["text"])
EOF
```

---

## 方案四：macOS 内置语音识别

macOS 自带语音识别功能，可以直接使用：

```bash
# 方法1：使用 macOS Dictation
# 系统偏好设置 → 键盘 → 听写 → 启用听写

# 方法2：使用 AppleScript（需要授予权限）
osascript -e 'tell app "SpeechRecognitionServer" to listen for speech'
```

---

## 方案五：云端 API（无需本地安装）

### OpenAI Whisper API
```bash
pip3 install openai

export OPENAI_API_KEY="你的Key"

python3 << 'EOF'
import openai
audio_file = open("/tmp/audio.wav", "rb")
transcript = openai.audio.transcriptions.create(
    model="whisper-1",
    file=audio_file,
    language="zh"
)
print(transcript.text)
EOF
```

### 费用
- Whisper API: $0.006/分钟（非常便宜）

---

## 🎯 快速开始建议

1. **先试方案一**：你的 faster-whisper 已安装，只需安装 socksio
2. **设置代理**：确保能访问 HuggingFace
3. **使用 tiny 模型**：减少等待时间

```bash
# 一键修复
pip3 install socksio

# 设置代理（如果需要）
export HTTP_PROXY=http://127.0.0.1:7890
export HTTPS_PROXY=http://127.0.0.1:7890
```

---

## 常见问题

**Q: 模型下载太慢？**
A: 使用代理，或选择 tiny 模型

**Q: 转录不准确？**
A: 尝试 larger 模型，或确保音频清晰

**Q: 支持哪些语言？**
A: faster-whisper 支持 100+ 语言，中文效果很好
