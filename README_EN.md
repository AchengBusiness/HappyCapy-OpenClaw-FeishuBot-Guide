# Build Your Feishu AI Assistant - OpenClaw Quick Start

> **Want AI assistant capabilities in your Feishu workspace?**
>
> With HappyCapy's powerful capabilities, you can deploy your own Feishu AI bot in just 10 minutes!

> **No deep programming knowledge required - let Capy generate the code for you:**
>
> - Smart conversations - chat like ChatGPT
> - Group chat summarization - extract key meeting points
> - Scheduled reminders - never miss important tasks
> - Web search - get real-time information

---

**Target Audience:** Feishu users, teams looking to integrate AI, HappyCapy newcomers

**Time Required:** 10-15 minutes

**Technical Requirements:** Almost zero coding knowledge needed

---

## Table of Contents

| Chapter | Content | Jump To |
|:--------|:--------|:--------|
| Chapter 1 | Prerequisites | [Click](#1-prerequisites) |
| Chapter 2 | Generate Code with HappyCapy | [Click](#2-generate-code-with-happycapy) |
| Chapter 3 | Bot Configuration Planning | [Click](#3-bot-configuration-planning) |
| Chapter 4 | AI Service Configuration | [Click](#4-ai-service-configuration) |
| Chapter 5 | Sandbox Deployment | [Click](#5-sandbox-deployment) |
| Chapter 6 | Feishu Backend Setup | [Click](#6-feishu-backend-setup) |
| Chapter 7 | How to Chat with Your Bot | [Click](#7-how-to-chat-with-your-bot) |
| Chapter 8 | How to Summarize Group Chats | [Click](#8-how-to-summarize-group-chats) |
| Chapter 9 | Troubleshooting | [Click](#9-troubleshooting) |

---

### Quick Links

| Platform | Link |
|:---------|:-----|
| **HappyCapy Website** | [https://happycapy.ai](https://happycapy.ai/signup?invite_ref=aGHAUcHN) |
| **Feishu Open Platform** | https://open.feishu.cn |
| **Claude API Console** | https://console.anthropic.com |
| **Google AI Studio** | https://makersuite.google.com/app/apikey |
| **Deepseek Platform** | https://platform.deepseek.com |
| **Qwen Console** | https://dashscope.console.aliyun.com |

---

## 1. Prerequisites

### 1.1 What You Need

Before starting, make sure you have:

- **Feishu Account** - With permission to create enterprise apps (admin or developer)

- **HappyCapy Account** - If you don't have one, sign up at the website
  - Website: [https://happycapy.ai](https://happycapy.ai/signup?invite_ref=aGHAUcHN)

- **15 minutes** - Follow the tutorial step by step

- **Third-party AI Service API Key** - For AI capabilities (see Chapter 4)

---

### 1.2 What You DON'T Need

- **Programming experience** - Capy writes the code for you

- **A server** - HappyCapy sandbox is ready for you

- **Complex configuration** - We'll guide you step by step

---

### 1.3 Credentials to Get from Feishu (Later)

**Feishu App Credentials** (Chapter 6 will teach you how to get these)

- App ID (format: `cli_xxxxxxxxxxxx`)
- App Secret (a long secret key)

---

**AI Service Credentials**

> **Important:** HappyCapy's built-in AI service doesn't support direct Feishu bot integration. You need to use a third-party AI service provider's API.
>
> Supported third-party AI services include:
> - Claude (Anthropic)
> - Gemini (Google)
> - Deepseek
> - Qwen (Alibaba Cloud)
> - OpenAI-compatible custom services
> - Claude-compatible custom services

---

## 2. Generate Code with HappyCapy

> **This is the most important step!** You don't need to write code yourself - Capy will generate all files for you.

---

### 2.1 Open HappyCapy Chat Interface

1. Log in to HappyCapy (website: [https://happycapy.ai](https://happycapy.ai/signup?invite_ref=aGHAUcHN))

2. Click "New Chat" or select an existing conversation

3. You'll see a ChatGPT-like chat interface

> **Tip:** HappyCapy's interface is similar to ChatGPT - conversation history on the left, chat window on the right. Just type your instructions and Capy will respond and execute in real-time.

---

### 2.2 Request Capy to Generate Project Structure

#### You should say:

```
Hi Capy! I want to deploy a Feishu bot in the HappyCapy sandbox with these features:
1. Smart conversations (AI-powered replies)
2. Group chat summarization
3. Support @mentions in group chats

Please help me:
1. Create the project directory structure
2. Generate the package.json file
3. Create a basic .env configuration template
```

---

#### Capy will respond:

Capy will understand your requirements and begin:

- Creating the project folder

- Generating `package.json` dependencies

- Creating `.env` environment variable template

**You'll see output like this:**

```bash
# Capy will execute these commands:
mkdir feishu-bot && cd feishu-bot
# Create package.json
# Create .env template
```

---

### 2.3 Request Core Code Files

#### You should say:

```
Great! Now please generate three core code files:

1. **server.js** - Main server file
   - Listen on port 4000 (to avoid common port conflicts)
   - Receive Feishu webhook messages
   - Handle message events and call AI for replies

2. **feishu.js** - Feishu API wrapper
   - Token management
   - Send messages (text and rich text)
   - Get group chat history
   - Get chat info

3. **agent.js** - AI conversation handler
   - Integrate third-party AI APIs (Claude, Deepseek, etc.)
   - Process user messages and generate replies
   - Support tool calls (group summarization feature)

Please create these three files with clean, commented code.
```

---

### 2.6 Expose Public Port

#### You should say:

```
Server started successfully! Now I need to:
1. Expose port 4000 to the internet (using /app/export-port.sh)
2. Get the public URL
3. Tell me this address - I need to configure it in Feishu backend
```

---

#### Capy will respond:

```bash
# Expose port
/app/export-port.sh 4000

# Result:
✅ Port exposed successfully!
🌐 Public URL: https://4000-xxxxxx-preview.happycapy.ai

Please configure this address in Feishu backend's event subscription:
- Event subscription URL: https://4000-xxxxxx-preview.happycapy.ai/webhook/event
```

---

> **Important: Copy and save this public URL! You'll need it for the next step.**

---

## 4. AI Service Configuration

> **Important:** HappyCapy's built-in AI service doesn't support direct Feishu bot integration. You need to use a third-party AI service provider's API.

---

### 4.1 Supported AI Service Providers

| Provider | Features | Best For |
|:---------|:---------|:---------|
| **Claude (Anthropic)** | High quality, safe & controllable | Enterprise apps, quality conversations |
| **Gemini (Google)** | Fast, generous free tier | Daily chat, cost-sensitive scenarios |
| **Deepseek** | Cost-effective, fast in China | Chinese users, high-frequency calls |
| **Qwen (Alibaba)** | Excellent Chinese understanding | Chinese content, domestic enterprises |
| **Custom (OpenAI-compatible)** | Flexible, local deployment | Private deployment, special needs |
| **Custom (Claude-compatible)** | Flexible, multi-platform | AWS Bedrock, Azure, etc. |

---

### 4.2 Claude (Anthropic) API Configuration

#### Get API Key

1. Visit Anthropic Console
   - Console URL: https://console.anthropic.com/
2. Log in or register
3. Go to "Settings" → "API Keys"
4. Click "Create Key" to create a new API Key
5. Copy the generated key (format: `sk-ant-api03-xxxxxxxxx...`)

---

#### .env Configuration Example

```env
# ===== Claude/Anthropic API Config =====

# API Key (required)
CLAUDE_API_KEY=sk-ant-api03-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

# API Base URL (optional, defaults to official)
CLAUDE_BASE_URL=https://api.anthropic.com

# Model name (required)
# Options: claude-opus-4-6 / claude-sonnet-4-5 / claude-haiku-3-5
CLAUDE_MODEL=claude-sonnet-4-5

# API version (recommended)
ANTHROPIC_API_VERSION=2023-06-01

# ===== General Config =====
BOT_NAME=My Feishu AI Assistant
PORT=4000
MAX_TOKENS=4096
TEMPERATURE=0.7
```

---

#### Model Selection Guide

| Model | Features | Best For | Cost |
|:------|:---------|:---------|:-----|
| `claude-opus-4-6` | Most powerful, best reasoning | Complex analysis, professional tasks | $$$ |
| `claude-sonnet-4-5` | Balanced performance & cost (recommended) | Daily chat, group summaries | $$ |
| `claude-haiku-3-5` | Lightweight, fastest, lowest cost | Simple Q&A, quick responses | $ |

---

### 4.4 Deepseek API Configuration

#### .env Configuration Example

```env
# ===== Deepseek API Config =====
# Note: Deepseek is compatible with OpenAI API format

# API Key (required)
OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxx

# API Base URL (required, fixed value)
OPENAI_BASE_URL=https://api.deepseek.com

# Model name (required)
# Options: deepseek-chat / deepseek-reasoner
OPENAI_MODEL=deepseek-chat

# ===== General Config =====
BOT_NAME=My Feishu Assistant
PORT=4000
API_TIMEOUT=60000
```

---

## 6. Feishu Backend Setup

> **Important:** Before this step, make sure:
>
> - Server is running (Chapter 5)
> - You have the public URL (Section 2.6)
> - The public URL is accessible

---

### 6.1 Create Feishu App

#### Step 1: Visit Feishu Open Platform

1. Open browser and visit Feishu Open Platform
   - URL: https://open.feishu.cn/

2. Log in with your Feishu account

3. Click "Developer Console" button in the top right

---

#### Step 2: Create Enterprise App

1. In the developer console, click "Create Enterprise App" (blue button)

2. Fill in the information:
   - **App Name:** My AI Assistant (or your preferred name, 4-8 characters recommended)
   - **App Description:** Intelligent Feishu bot based on OpenClaw, supporting smart chat and group summarization
   - **App Icon:** Upload a square icon (512x512px recommended, PNG/JPG, <200KB)

3. Click "Create"

---

### 6.3 Configure Event Subscription (Critical Step!)

> **This is the most critical step!** Wrong configuration will prevent the bot from receiving messages.

---

#### Fill in Request URL

```
https://4000-xxxxxx-preview.happycapy.ai/webhook/event
```

> **Important:** Replace `4000-xxxxxx-preview.happycapy.ai` with your actual public URL, and add `/webhook/event` at the end

---

#### Subscribe to Event Type

Search and add: `im.message.receive_v1`

---

## 7. How to Chat with Your Bot

### 7.1 Add the Bot

1. Open Feishu client (desktop or mobile)

2. Click "+" button in the top left

3. Select "Add Bot"

4. Search for your bot name

5. Click "Add"

---

### 7.2 Chat Examples

**Example 1: Greeting**

```
You: Hello
Bot: Hello! I'm your AI assistant. How can I help you?

You: What can you do?
Bot: I can help you with:
     - Smart chat - answer questions, provide suggestions
     - Group summarization - extract meeting highlights
     - Web search - get real-time information
     - Run code - execute Python/JavaScript
     - Create documents - generate Feishu docs

     Just tell me what you need!
```

---

### 7.3 Use in Group Chats

In group chats, you need to @mention the bot to trigger a response:

```
@MyAIAssistant Hello!
```

The bot will reply:

```
Hello everyone! I'm the AI assistant. Happy to join this group.
If you need help, just @mention me anytime!
```

---

## 8. How to Summarize Group Chats

> **This is one of the most useful features!** Quickly extract discussion highlights and save reading time.

---

### 8.1 Basic Summary

#### In group chat:

```
@MyAIAssistant summarize today's discussion
```

---

### 8.2 Specify Time Range

| You say | Time range |
|:--------|:-----------|
| "summarize last 1 hour" | Last 1 hour of messages |
| "summarize last 3 hours" | Last 3 hours of messages |
| "summarize today" | Today 00:00 to now |
| "summarize yesterday" | All of yesterday |
| "summarize this week" | This Monday to now |
| "summarize all" | All history |

---

## 9. Troubleshooting

### Problem 1: Bot Not Responding

**Symptom:** Messages sent to bot get no reply

---

**Troubleshooting Steps:**

**1. Check server status**

Say to Capy:
```
Please check if the Feishu bot server is still running, check process status
```

---

**2. Check logs**

Say to Capy:
```
Check recent error logs for any anomalies
```

---

**3. Check Feishu configuration**

- Is the "Event Subscription" URL verified in Feishu backend?
- Are permissions approved?
- Is the app published?

---

### Problem 4: Port Exposure Failed

**Symptom:** Public URL not accessible, Feishu verification fails

**Cause:** Port mapping may expire after HappyCapy sandbox restart

---

**Solution:**

Say to Capy:
```
Re-expose port 4000 and give me the new public URL
```

Capy will execute:
```bash
/app/export-port.sh 4000
```

Then:

1. Copy the new public URL

2. Update the "Event Subscription" request URL in Feishu backend

3. Re-verify

---

## Congratulations!

If you've completed all the steps above, you now have a fully functional Feishu AI bot!

---

### What You Can Do Now:

- Smart conversations with the bot

- @mention the bot in group chats

- Quick group chat summarization

- AI-powered web search

- Generate Feishu documents

---

## Resources

### Official Documentation

| Document | Link |
|:---------|:-----|
| Feishu Open Platform Docs | https://open.feishu.cn/document |
| Claude API Docs | https://docs.anthropic.com/claude/reference |
| Gemini API Docs | https://ai.google.dev/docs |
| Deepseek API Docs | https://platform.deepseek.com |
| Qwen API Docs | https://help.aliyun.com/zh/dashscope/ |
| HappyCapy Guide | [https://happycapy.ai/docs](https://happycapy.ai/signup?invite_ref=aGHAUcHN) |

---

**Enjoy using your new AI assistant!**

---

**Document Version:** v1.1.0

**Last Updated:** 2026-02-28

**Author:** Acheng ([https://github.com/AchengBusiness](https://github.com/AchengBusiness))

**Environment:** HappyCapy Sandbox + Feishu Open Platform

**License:** MIT
