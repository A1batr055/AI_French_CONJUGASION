# AI Conjugaison（多模型）
法语动词变位练习站点。零后端，Key只保存在浏览器本地。

直链：https://a1batr055.github.io/AI_French_CONJUGAISON/

> ⚠️ 必要条件：**需要科学上网**。  
> 无后端代理的前端直连会暴露 API Key，请自行评估风险。
> 本项目和README由AI辅助生成。

---

## 功能速览
- 自建分组词库；动词可在分组间移动  
- 练习出题（按 CEFR 等级与时态）；每动词固定 6 题（六个人称）  
- 变位表弹窗（Présent / Passé Composé / Imparfait / Futur Simple 等）  
- 多家 LLM 可选：**OpenRouter（含免费模型）/ OpenAI / Google Gemini / DeepSeek / 自定义**

---

## 最快上手（推荐用 OpenRouter 免费模型）
1. 访问 **openrouter.ai** 注册并创建 API Key。 [oai_citation:0‡OpenRouter](https://openrouter.ai/docs/quickstart?utm_source=chatgpt.com)  
2. 打开本站 → 进入“设置” → 选择提供商 **OpenRouter** → 粘贴 Key。  
3. 在“模型”里选 **免费分组（:free）** 任一模型 → 保存设置。  
4. 切到“练习”，选择等级、时态、词源 → 生成题目。

> 免费模型清单（精简常用；如变动以 OpenRouter 目录为准）：  
> - `google/gemini-2.0-flash-exp:free`（Gemini 免费变体）  
> - `openai/gpt-oss-20b:free`、`openai/gpt-oss-120b:free`（OpenAI 开放权重系）  
> - `deepseek/deepseek-chat:free`  
> - `mistralai/mistral-small:free`

**OpenRouter 免费额度（官方规则）**  
- `:free` 模型：**20 次/分钟**；  
- 账户购买 < \$10：**50 次/天**；购买 ≥ \$10：**1000 次/天**（仅针对 `:free` 模型）。 [oai_citation:1‡OpenRouter](https://openrouter.ai/pricing?utm_source=chatgpt.com)

> 说明：调用次数按“**请求数**”计，不按生成题量计。例如你点“生成题目”一次=1次，再点“查看变位表”一次=1次。

---

## 其他提供商（可选）
- **OpenAI（ChatGPT 家族）**：需要 OpenAI API Key。  
- **Google Gemini**：需要 Google API Key。近期**免费配额与限速频繁调整**，如出现 429 等报错，请以 **Gemini 官方“Rate limits”文档与控制台**为准。 [oai_citation:2‡Google AI for Developers](https://ai.google.dev/gemini-api/docs/rate-limits?utm_source=chatgpt.com)  
- **DeepSeek**：需要 DeepSeek API Key。  
- **自定义**：可填自有兼容 OpenAI 协议的网关 Base URL 与模型 ID。

---

## 常见报错与处理
**一键排障三步**：**刷新页面 → 换节点（代理） → 换网络/流量**。  
若仍失败，结合错误码处理：

- **429 / RESOURCE_EXHAUSTED / rate limit / quota**  
  - 说明：被限流或免费额度用尽。  
  - 处理：等 1–5 分钟重试；换模型（或非高峰时段）；OpenRouter 充值≥\$10 可将 `:free` 模型日限额提到 1000 次。 [oai_citation:3‡OpenRouter](https://openrouter.ai/docs/api/reference/limits?utm_source=chatgpt.com)  
  - Gemini 近期免费额度收紧属**常态**，请以官方文档与控制台显示为准。 [oai_citation:4‡Google AI for Developers](https://ai.google.dev/gemini-api/docs/rate-limits?utm_source=chatgpt.com)
- **401 / unauthorized / invalid key**  
  - 说明：Key 无效或未授权。  
  - 处理：检查复制是否完整；确认选对提供商；必要时重建 Key。 [oai_citation:5‡OpenRouter](https://openrouter.ai/docs/api/reference/authentication?utm_source=chatgpt.com)
- **404 / model_not_found**  
  - 说明：模型 ID 不存在或不再开放。  
  - 处理：切换到页面已内置的推荐/免费模型。  
- **400 / bad request / 参数错误**  
  - 说明：请求体不合规（例如自定义模型 ID 或 Base URL 写错）。  
  - 处理：恢复默认；仅改“提供商+模型”两项再试。  
- **5xx / upstream error**  
  - 说明：上游不稳定。  
  - 处理：换一个免费模型或稍后重试。

> 扩展阅读：OpenRouter Chat Completions 规范与用法。 [oai_citation:6‡OpenRouter](https://openrouter.ai/docs/api/reference/overview?utm_source=chatgpt.com)

---

## 费用与安全
- 使用 **OpenRouter 免费模型**不收费，但受速率与日配额限制。转用非免费模型，**按模型标价**计费。配额与价格以 OpenRouter 页面为准。 [oai_citation:7‡OpenRouter](https://openrouter.ai/pricing?utm_source=chatgpt.com)  
- 本站为**纯前端**：API Key 存储在你的浏览器 `localStorage`；开发与生产请谨慎，**不要在公共环境暴露 Key**。  
- 生产场景建议加自有后端代理，统一保管 Key 与做限流。

---

## 常见问题（FAQ）
**Q1：免费 50 次/天是按“生成题目数量”还是“请求数”？**  
A：按**请求数**。一次按钮调用=一次请求。 [oai_citation:8‡OpenRouter](https://openrouter.ai/docs/api/reference/limits?utm_source=chatgpt.com)

**Q2：Gemini 为什么老报 429？**  
A：多为**额度或限速**触发。Gemini 免费层政策近期调整频繁，详情以官方“Rate limits”与控制台显示为准。 [oai_citation:9‡Google AI for Developers](https://ai.google.dev/gemini-api/docs/rate-limits?utm_source=chatgpt.com)

**Q3：我的模型怎么没在下拉里？**  
A：免费清单经常变化；保留了几家**稳定常用**的。你也可以切到“自定义模型 ID”。（OpenRouter 实现兼容 OpenAI 的 `/chat/completions` 协议。） [oai_citation:10‡OpenRouter](https://openrouter.ai/docs/faq?utm_source=chatgpt.com)

**Q4：如何清除本地数据？**  
A：浏览器控制台执行：  
```js
localStorage.removeItem('llm_settings'); 
localStorage.removeItem('verb_groups');
或清空网站存储后刷新。
