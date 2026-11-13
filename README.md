
# AI-Development-Task

基于 n8n、GitHub Actions 和 OpenAI Codex 的半自动 AI 软件开发实验项目。

## 项目目标

通过 AI 自动完成需求分析、代码生成、测试和 Pull Request 创建。

## 技术栈

- Python
- FastAPI
- pytest

## 开发规范

- 所有新功能必须在独立分支开发。
- 必须编写基础测试。
- 不允许直接修改 main 分支。
- 所有代码修改通过 Pull Request 审核。

## 本地运行

需要 Python 3.10 或更高版本。以下命令均在仓库根目录执行。

### 安装依赖

创建并激活虚拟环境：

```bash
python -m venv .venv
source .venv/bin/activate
```

Windows PowerShell 使用 `.venv\Scripts\Activate.ps1` 激活虚拟环境。

```bash
python -m pip install -r requirements.txt
```

`requirements.txt` 包含 FastAPI、Uvicorn、pytest，以及测试客户端需要的 HTTPX。

### 启动项目

```bash
python -m uvicorn main:app --reload
```

服务默认地址为 <http://127.0.0.1:8000>，交互式 API 文档位于
<http://127.0.0.1:8000/docs>。`--reload` 适用于本地开发。

### 健康检查

```bash
curl http://127.0.0.1:8000/health
```

`GET /health` 返回 HTTP 200 和以下 JSON：

```json
{"status": "ok"}
```

### 运行测试

```bash
python -m pytest -q
```

测试使用 FastAPI 的 `TestClient` 验证响应状态码、JSON 内容类型和响应内容，
无需事先启动 Uvicorn。

## 文件结构

```text
.
├── .gitignore
├── README.md
├── main.py
├── requirements.txt
└── tests/
    └── test_health.py
```
