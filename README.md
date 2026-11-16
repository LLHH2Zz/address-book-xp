[README.md](https://github.com/user-attachments/files/34918909/README.md)
# 通讯录 Address Book

一个基于 FastAPI + 原生前端实现的通讯录管理系统，支持联系人增删改查、收藏标记、多条联系方式管理以及 Excel 导入导出。本项目为极限编程（XP）结对作业。

## 功能特性

- 联系人增删改查（CRUD）
- 联系人收藏 / 取消收藏
- 一个联系人支持多条联系方式（一对多）
- Excel 导入 / 导出
- FastAPI 自动生成的 `/docs` 在线接口文档

## 技术栈

| 分层 | 技术 |
| --- | --- |
| 后端 | Python + FastAPI + SQLite + openpyxl |
| 前端 | 原生 HTML + CSS + JavaScript（fetch） |
| 版本控制 | Git + GitHub |

## 目录结构

```
address-book-xp/
├── main.py          # 后端入口，全部 Restful 接口
├── index.html       # 前端页面（含 CSS 与 JS 交互逻辑）
└── README.md        # 项目说明文档
```

## 数据库设计

两张数据表，一个联系人可对应多条联系方式（一对多）：

- `contact` 联系人表：`id`、`name`、`is_bookmark`（收藏标记）
- `contact_method` 联系方式表：`id`、`contact_id`（外键）、`method_type`、`content`

## 接口文档

| 请求方法 | 接口地址 | 功能说明 |
| --- | --- | --- |
| POST | /api/contact | 新增联系人 |
| GET | /api/contact | 查询全部联系人 |
| DELETE | /api/contact/{id} | 删除联系人 |
| PUT | /api/contact/{id} | 修改联系人收藏状态 |
| POST | /api/contact/{cid}/method | 添加联系方式 |
| DELETE | /api/method/{mid} | 删除单条联系方式 |
| GET | /api/excel/export | 导出 Excel |
| POST | /api/excel/import | 导入 Excel |

## 快速开始

### 环境要求

- Python 3.8+

### 安装依赖

```bash
pip install fastapi uvicorn openpyxl
```

### 启动后端

```bash
uvicorn main:app --reload
```

启动后访问：

- 前端页面：http://127.0.0.1:8000/
- 接口文档：http://127.0.0.1:8000/docs


## 团队成员与分工

| 成员 | 学号 | 分工 | 贡献 |
| --- | --- | --- | --- |
| 何景豪 | 832401307 | 后端开发：数据库设计、全部接口、Excel 导入导出、README | 50% |
| 李昊泽 | 832401309 | 前端开发：index.html 页面布局、表单交互、JS 调用接口 | 50% |

## 迭代提交记录

迭代 1 ： 后端基础接口，联系人增删改查 main.py 
迭代 2 ：前端页面，对接后端接口  index.html 
迭代 3 ：补充项目说明文档，前后端联调完成  README.md 

