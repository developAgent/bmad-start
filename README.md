# bmad-start
BMAD Method 最佳实践项目模板

## 什么是 BMAD Method
BMAD Method 是一套面向AI驱动开发的完整方法论体系，提供了从需求分析、产品设计、开发实现到测试部署的全流程工具链和最佳实践。它通过多智能体协作、标准化工作流和可复用模块，大幅提升软件开发效率和质量。

## 核心模块

### 🧱 Core - 核心模块
核心模块提供BMAD Method的基础能力和通用工具：
- **Brainstorming (BSP)**：创意头脑风暴工具，适用于项目早期构思或遇到瓶颈时生成创意
- **Party Mode (PM)**：多智能体协作模式，支持多角色Agent共同讨论和协作
- **BMad Help (BH)**：帮助和文档查询工具
- **Index Docs (ID)**：文档索引工具，帮助LLM快速理解项目文档结构
- **Shard Document (SD)**：大文档分片工具，处理超过500行的大型文档
- **Editorial Review (EP/ES)**：文档审核工具，支持内容和结构双维度审核
- **Adversarial Review (AR)**：对抗性质量评审，用于交付前的质量保障
- **Edge Case Hunter (ECH)**：边界用例检测工具，与对抗性评审配合提供正交覆盖
- **Distillator (DG)**：文档蒸馏工具，生成Token高效的精简版本供下游LLM使用

### 🏗️ BMB - BMad Builder 构建模块
Builder模块用于创建和扩展BMAD生态的组件：
- **Setup Builder Module (SB)**：安装或更新Builder模块配置
- **Agent Builder (BA/AA)**：智能体构建工具，支持创建、编辑和分析Agent技能
- **Workflow Builder (BW/AW/CW)**：工作流构建工具，支持创建、编辑、分析和转换工作流
- **Module Builder (IM/CM/VM)**：模块构建工具，支持构思、创建和验证BMAD模块

### 📋 BMM - BMad Method 方法模块
Method模块提供完整的产品开发方法论和工作流：
- **分析阶段**：需求调研、市场分析、用户研究
- **规划阶段**：路线图制定、史诗/用户故事拆分、工作计划
- **解决方案阶段**：架构设计、产品设计、技术方案选型
- **实现阶段**：开发实现、集成测试、交付部署

### 💡 CIS - Creative Innovation Studio 创新工作室模块
CIS模块专注于创意和创新工作流：
- 设计思维方法论支持
- 创新战略规划
- 问题解决工作坊
- 创意讲故事和演示设计
- 创意教练指导

### 🎮 GDS - Game Development Studio 游戏开发模块
GDS模块提供游戏开发全流程支持：
- 游戏概念设计和GDD（游戏设计文档）编写
- 游戏架构设计
- 叙事和剧情设计
- 游戏开发工作流
- 测试和玩测计划
- 性能优化和发布支持

### 🧪 TEA - Test Architecture 测试架构模块
TEA模块提供完整的测试和质量保障体系：
- 测试架构设计
- 自动化测试框架
- 端到端测试生成
- CI/CD测试集成
- 非功能需求测试
- 测试用例设计和评审
- 测试追踪和覆盖率分析

## 快速开始
1. 克隆此项目作为基础模板
2. 根据你的项目需求选择启用对应的模块
3. 运行`/bmad-help`获取各模块的使用帮助
4. 开始你的AI驱动开发之旅！

## 更多资源
- 官方文档：https://docs.bmad-method.org/
- Builder模块文档：https://bmad-builder-docs.bmad-method.org/
- 测试架构文档：https://bmad-code-org.github.io/bmad-method-test-architecture-enterprise/
