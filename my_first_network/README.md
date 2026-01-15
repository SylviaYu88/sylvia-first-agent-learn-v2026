# Default Workspace

A simple OpenAgents network to get you started.

## Overview

基于 OpenAgents + 智谱 GLM-4-plus 开发的求职辅助智能体，包含4个功能独立又可协同的智能体，覆盖「简历翻译→简历优化→面试辅导→薪资测算」全流程，完美适配制造业工艺工程师/测试工程师等岗位的求职需求。

## Agents

| Agent | Type | Description |
|-------|------|-------------|
| `interview-coach` | YAML (LLM) | 资深面试辅导专家，生成岗位高频面试题+STAR回答模板+薪资谈判策略 |
| `resume-editor` | YAML (LLM) | 简历优化专家，基于STAR法则优化简历+JD关键词匹配+中英文简历润色 |
| `resume-translator` | YAML (LLM) | 专业简历翻译专家，中译英简历翻译，适配欧美/新加坡等地区简历规范 |
 `salary-calculato` | YAML (LLM) | 薪资测算专家，精准计算税后薪资+福利明细+年终奖扣税 |


## Quick Start

### 1. Start the Network

```bash
openagents network start .
```

### 2. Access Studio

Open your browser to:
- **http://localhost:8700/studio/** - Studio web interface
- **http://localhost:8700/mcp** - MCP protocol endpoint

### 3. Launch an Agent

Choose one of the agents:

**YAML Agent (recommended for beginners):**
```bash
openagents agent start agents/interview-coach
```

**Python Agent (basic):**
```bash
python agents/simple_agent.py
```

**Python Agent (with LLM):**
```bash
# Set your OpenAI API key first
export OPENAI_API_KEY=your-api-key
export OPENAI_BASE_URL
python agents/llm_agent.py
```

> **Note:** LLM-powered agents (charlie.yaml and llm_agent.py) require an OpenAI API key.

### 4. Say Hello!

Post a message to the `general` channel and the agent will respond!

## Configuration

- **Network Port:** 8700 (HTTP), 8600 (gRPC)
- **Studio:** http://localhost:8700/studio/
- **MCP:** http://localhost:8700/mcp
- **Channel:** `general`

## Agent Groups & Authentication

This network has several agent groups configured:

| Group | Password | Description |
|-------|----------|-------------|
| `guest` | (none) | Default group, no password required |
| `admin` | `admin` | Full permissions to all features |
| `coordinators` | `coordinators` | For router/coordinator agents |
| `researchers` | `researchers` | For worker/research agents |

### Logging in as Admin

To access admin features in Studio:

1. Open http://localhost:8700/studio/
2. Click on the group selector (or login)
3. Select group: **admin**
4. Enter password: **admin**

### Admin Features

As an admin, you have full permissions including:

- Access to all channels and messaging features
- Create, edit, and delete forum topics
- Manage wiki pages and approve edit proposals
- Create and manage shared caches
- Full access to all mod features

## Next Steps

- Customize `network.yaml` to add more channels or mods
- Create your own agents by copying the examples
- Check out the demos in the `demos/` folder for more advanced patterns
- Visit [openagents.org/docs](https://openagents.org/docs/) for full documentation
