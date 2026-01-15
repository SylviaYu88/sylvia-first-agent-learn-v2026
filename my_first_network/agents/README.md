# 🤖 求职全链路智能体套件 (4个智能体协同运行)
基于 OpenAgents + 智谱 GLM-4-plus 开发的求职辅助智能体，适配制造业工艺工程师等岗位，无429限流报错，响应速度快。

## 📌 包含4个智能体
1. interview-coach：面试辅导专家 → 高频面试题+STAR回答模板+薪资谈判话术
2. resume-editor：简历优化专家 → STAR法则优化+JD关键词匹配+中英文简历润色
3. resume-translator：简历翻译专家 → 中译英简历，适配欧美/新加坡求职规范
4. salary-calculator：薪资测算专家 → 精准税后薪资计算+年终奖扣税+多地区对比

## 🚀 快速启动（Mac/Linux通用）
### 前置要求
1. 已安装OpenAgents框架
2. 获取智谱GLM API_KEY（https://open.bigmodel.cn/）
3. 修改所有yaml文件中的 api_key 为你的真实密钥

### 启动命令
```bash
# 1. 清理残留进程
pkill -9 -f openagents
# 2. 启动核心服务（新开终端窗口保持打开）
openagents network start --port 8700
# 3. 串行启动4个智能体，无并发冲突
cd /Users/yuyan/my_first_network/agents
openagents agent start interview-coach.yaml && sleep 3
openagents agent start resume-editor.yaml && sleep 3
openagents agent start resume-translator.yaml && sleep 3
openagents agent start salary-calculator.yaml
