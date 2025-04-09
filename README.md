 
# spring-ai



#  heima-ai 智能对话系统

## 项目简介
基于Spring AI构建的智能对话系统，整合多种AI能力与自定义记忆管理，提供以下核心功能：
- 多模型对话（支持Ollama/OpenAI）
- PDF文档向量化与语义搜索
- 对话历史管理（内存/Redis存储）
- 向量相似度计算工具
- RESTful API接口

## 技术栈
- **核心框架**: 
  - Spring Boot 3.4.3
  - Spring AI 1.0.0-M6
- **AI 能力**:
  - Ollama 本地模型集成 ([`ChatController`](file://heima-ai/src/main/java/com/itheima/ai/controller/ChatController.java#L18-L69))
  - OpenAI 云服务集成
  - 文本向量化处理 ([`VectorDistanceUtils`](file://heima-ai/src/main/java/com/itheima/ai/utils/VectorDistanceUtils.java#L2-L75))
- **数据存储**:
  - Redis 对话记忆管理 ([`RedisChatMemory`](file://heima-ai/src/main/java/com/itheima/ai/repository/RedisChatMemory.java#L12-L56))
  - MySQL 连接支持（需配置）
- **其他**:
  - Lombok 注解处理
  - JUnit 5 单元测试
  - Spring Data Redis

## 快速开始
1. 环境要求：
   - JDK 17
   - Redis 服务（配置见`application.yaml`）
   - Ollama 本地服务（可选）

2. 基础配置：
```yaml
spring:
  ai:
    ollama:
      base-url: http://localhost:11434  # Ollama服务地址
      chat:
        model: deepseek-r1:7b  # 使用模型
  data:
    redis:
      host: 192.168.150.101  # Redis服务器地址
```


---

### 变更规划 2：添加API接口说明
**变更说明**:
补充主要接口文档说明

**变更内容**:
## 接口说明
### 对话服务
- `POST /ai/chat`
  - 参数: 
    - `message`: 用户消息
    - `files`: 支持多文件上传（PDF处理）
  - 功能: 智能对话与文档分析

### 历史记录
- `GET /ai/history/{sessionId}`
  - 功能: 获取指定会话的聊天记录
  - 返回: List<`MessageVO`> ([定义](file://heima-ai/src/main/java/com/itheima/ai/entity/vo/MessageVO.java#L6-L21))


---

### 变更总结
1. 创建完整的项目说明文档结构
2. 明确技术组件及其对应实现类
3. 添加核心配置示例
4. 补充主要接口文档
5. 通过代码片段链接增强文档可追溯性

文档覆盖了项目核心功能模块、技术选型依据及基础使用说明，便于新开发者快速理解项目架构与核心实现。

