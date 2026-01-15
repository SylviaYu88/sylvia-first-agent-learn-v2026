# sylvia-first-agent-learn-v2026
# 🤖 求职全链路智能体套件（4智能体协同）
基于 OpenAgents + 智谱 GLM-4-plus 开发的求职辅助智能体集群，覆盖「简历翻译→简历优化→面试辅导→薪资测算」全流程，适配制造业工艺工程师等技术岗位，支持中英文求职场景，无并发限流，一键启动可用。
## 📁 项目核心资源
| 资源类型                | 访问链接                                                                 | 功能说明                                  |
|-------------------------|--------------------------------------------------------------------------|-------------------------------------------|
| GitHub 仓库主页         | [SylviaYu88/sylvia-first-agent-learn-v2026](https://github.com/SylviaYu88/sylvia-first-agent-learn-v2026) | 查看项目结构、克隆/分支管理、提交记录      |
| 项目一键下载            | [项目ZIP压缩包](https://github.com/SylviaYu88/sylvia-first-agent-learn-v2026/archive/refs/heads/main.zip) | 无需Git，直接下载所有配置文件              |
| 面试教练配置文件        | [interview-coach.yaml](https://github.com/SylviaYu88/sylvia-first-agent-learn-v2026/blob/main/interview-coach.yaml) | 面试题生成、薪资谈判话术核心配置          |
| 问题反馈/需求提交       | [提交Issues](https://github.com/SylviaYu88/sylvia-first-agent-learn-v2026/issues/new) | 报告Bug、提出新功能需求                   |
| 智谱API-KEY申请         | [智谱开放平台](https://open.bigmodel.cn/)                                 | 获取项目所需的GLM模型密钥                  |
## 🚀 快速启动（Mac/Linux 通用）
### 前置依赖（必做）
1. 已安装 OpenAgents 框架（安装命令：`pip install openagents`）
2. 获取智谱 GLM API-KEY（[申请地址](https://open.bigmodel.cn/)）
3. 替换所有 `*.yaml` 文件中的占位符 `api_key: "请替换为你的密钥"` 为真实密钥

### 启动步骤
1. 清理残留进程（避免端口占用）
2. 启动 OpenAgents 核心服务
3. 串行启动4个智能体（避免并发限流）

### 完整启动命令（复制即用）
```bash
# 1. 清理残留进程
pkill -9 -f openagents

# 2. 启动核心服务（新开终端窗口，保持运行）
openagents network start --port 8700

# 3. 进入项目目录并启动智能体
cd /Users/yuyan/my_first_network/agents
openagents agent start interview-coach.yaml && sleep 3
openagents agent start resume-editor.yaml && sleep 3
openagents agent start resume-translator.yaml && sleep 3
openagents agent start salary-negotiator.yaml
```
## ✨ 核心功能亮点
| 智能体名称              | 核心能力                                                                 | 适配场景                                  |
|-------------------------|--------------------------------------------------------------------------|-------------------------------------------|
| resume-translator       | 中英简历互译、适配欧美/新加坡简历规范、自动剔除敏感信息（年龄/籍贯）       | 海外求职、外企中英文简历准备              |
| resume-editor           | STAR法则重构工作经历、量化成果、植入JD关键词、精简冗余内容                | 简历优化、提升HR初筛通过率                |
| interview-coach         | 分岗位生成高频面试题+STAR回答模板、薪资谈判全流程话术、面试避坑指南       | 技术岗面试准备、薪资谈判                  |
| salary-negotiator       | 税前税后薪资换算、年终奖扣税计算、多地区（中美/新加坡）薪资对比           | 谈薪前薪资测算、目标薪资反推              |
## 📌 完整使用流程（求职全链路）
1. **简历准备阶段**：用「resume-translator」将中文简历翻译成英文（适配海外岗位）→ 用「resume-editor」优化简历，植入JD关键词，生成投递版简历。
2. **面试准备阶段**：向「interview-coach」上传优化后的简历，获取该岗位的高频面试题、STAR回答模板、英文面试话术。
3. **谈薪阶段**：用「salary-negotiator」测算目标岗位的税后薪资（输入税前薪资+地区）→ 结合「interview-coach」的谈判话术，向HR提出薪资期望。
## 🛠️ 常见问题（FAQ）
### Q1：启动智能体后，发送消息无回复，终端无日志？
A1：用调试模式启动，强制输出所有日志，排查问题：
```bash
openagents agent start interview-coach.yaml -vvv
```
同时检查 `yaml` 文件中是否配置 `print_all_responses: true`（确保终端显示回复）。

### Q2：启动后出现 429 限流报错？
A2：429 是智谱API并发限制，解决方案：
1. 确保按教程「串行启动」智能体（间隔3秒），避免同时启动多个；
2. 检查 `yaml` 文件中是否配置：
   ```yaml
   max_concurrent_requests: 1
   request_interval: 2.0
   retry_on_rate_limit: true
   ```

### Q3：替换 API-KEY 后，仍提示「密钥无效」？
A3：1. 检查密钥是否复制完整（无多余空格/换行）；
2. 确认密钥适配 GLM-4-plus 模型（智谱密钥通用，若失效需重新申请）；
3. 重启智能体（修改配置后需重启生效）。

## 🤝 开源协作
欢迎开发者 Fork 本仓库进行二次开发，共同完善智能体功能！

### 贡献指南
1. Fork 本仓库到你的 GitHub 账号；
2. 创建分支（如 `feat/add-cover-letter-agent`），开发新功能（如新增求职信智能体）；
3. 提交代码并推送至你的 Fork 仓库；
4. 提交 Pull Request 到本仓库的 main 分支，描述清楚修改内容。

### 需求建议
如需新增功能（如面试复盘智能体、外企文化适配），可直接提交 [Issues](https://github.com/SylviaYu88/sylvia-first-agent-learn-v2026/issues/new)，说明需求场景和核心功能。
## 📋 附录
### 版本信息
- 项目版本：v1.0.0
- 适配框架：OpenAgents latest
- 适配模型：智谱 GLM-4-plus / GLM-4.7
- 最后更新时间：2026-01-15

### 免责声明
1. 本项目为开源学习用途，请勿用于商业盈利；
2. 请妥善保管个人 API-KEY，避免泄露（项目已做占位符脱敏，上传时请勿替换为真实密钥）；
3. 薪资测算结果基于公开税收政策，仅供参考，具体以企业实际发放为准。
