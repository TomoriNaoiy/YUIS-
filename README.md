# YUIS (You Upload, I Support) 

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-0.109+-009688.svg)
![DeepSeek](https://img.shields.io/badge/AI-DeepSeek%20V3-blueviolet)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

> **"You Upload, I Support."** —— 帮助你解决大学期末考只有复习资料没有卷子的苦恼。

**YUIS** 是一个基于 **RAG** 架构的教育辅助系统。他能够根据你提供的文档进行分析并给你出卷

---

## 📸 项目预览

<img width="2111" height="1304" alt="image" src="https://github.com/user-attachments/assets/24edea9d-d14e-4126-8d62-1f8578bb3261" />


---

## ✨ 核心亮点 (Key Features)
### 🧠 双阶段高精度检索
不仅仅是简单的向量相似度匹配。YUIS 采用了 **FAISS (召回) + FlagEmbedding (重排序)** 的双阶段管道架构。
### 🌐 混合知识体系
- **本地知识**：深度解析 PDF/Word/TXT 格式的非结构化数据。
- **联网补充**：集成 **DDGS**，当本地资料不足时，联网搜索知识点进行补充
### ⚡ 全异步高性能架构
拒绝卡顿。基于 **FastAPI** 的全异步设计。
- 利用 Python `asyncio` 实现 I/O 操作（如 API 调用、文件读写）的非阻塞处理。
- 单线程即可支撑高并发请求，在等待大模型生成的几十秒内，依然能流畅响应界面交互。


---

## 🛠️ 技术栈
* **后端框架**: FastAPI, Uvicorn, Python 3.10+
* **LLM 基座**: DeepSeek-V3 (via OpenAI Compatible API)
* **RAG 组件**: LangChain, FAISS (Vector DB), FlagEmbedding (Rerank)
* **深度学习**: PyTorch, Transformers, Sentence-Transformers
* **前端界面**: HTML5, Tailwind CSS, JavaScript (Vanilla)
* **部署运维**: Docker, Docker Compose

---

## 🚀 快速开始 (Quick Start)



### 本地开发运行 (使用 uv)

推荐使用 `uv` 进行极速依赖安装。

1.  **环境配置**
    ```bash
    # 创建虚拟环境
    uv venv
    
    # 激活环境 (Windows)
    .venv\Scripts\activate
    # 激活环境 (Mac/Linux)
    source .venv/bin/activate
    ```

2.  **安装依赖**
    ```bash
    uv pip install -r requirements.txt
    ```

3.**在.env.example中输入你的deepseek API KEY（便宜得很 直接去deepeek的API界面爆点金币就行）**

4.  **运行项目**
    ```bash
    python main.py
    ```
    终端显示 `Uvicorn running on http://0.0.0.0:8000` 即代表启动成功。


---

## 📖 使用指南

1.  **投喂资料**：在左侧面板上传你的复习资料（支持 PDF, Word）。
2.  **配置出题**：选择题目数量（选择/填空/简答）及考查主题。
3.  **生成试卷**：点击“生成试卷”，等待 AI 进行检索与重排序。
4.  **交互练习**：在右侧面板进行答题，点击选项查看正确答案与解析。
5.  **清空记忆**：更换学科前，请点击左侧的“清空”按钮重置知识库。

---

## 📂 项目结构

```text
YUIS/
├── main.py              # 程序入口
├── endpoints.py         # API 路由定义
├── endpoints/           # 业务逻辑实现
├── templates/           # 前端 HTML 页面
│   └── index.html
├── static/              # 静态资源 (图片/CSS/JS)
│   └── elain.png
├── data/                # 存放上传的临时文件 
├── faiss_store/         # 向量数据库索引文件
├── requirements.txt     # 项目依赖列表
├── docker-compose.yml   # Docker 编排文件
├── Dockerfile           # Docker 构建文件
└── .env                 # 环境变量
