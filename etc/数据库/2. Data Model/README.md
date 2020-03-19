# Data Model

数据模型（data model）是一种模型，是对现实世界数据特征的抽象。也就是说，数据模型是用来描述数据、组织数据和对数据进行操作的。

现有数据库均是基于某种数据库模型的。数据库模型是数据库系统的核心和基础。

### :package: 两类数据模型

数据模型应满足三方面要求：

- 比较真实地模拟现实世界。
- 容易为人所理解
- 便于在计算机上实现

如同在:building_construction:建筑设计的不同阶段需要不同的图纸:page_with_curl: 一样，在开发实施数据库应用系统中也需要使用不同的数据模型：**概念模型**、**逻辑模型**、**物理模型**。

<img src="..\..\..\pictures\Different_Level_of_abstraction_of_datamodel.png" style="width:80%;" />

根据模型应用的不同目的，可以将这些模型分为两大类，它们分别属于两个不同的层次：

- 概念模型（conceptual model）：按用户观点来对数据库和信息进行建模。主要用于数据库设计。

  [^]: 也称为信息模型。

- 逻辑模型和物理模型
  - 逻辑模型（logical model）：按照计算机系统的观点对数据建模，主要用于数据库管理系统的实现。
    - 层次模型（hierarchical model）
    - 网状模型（network model）
    - **关系模型**（relational model）
    - 面向对象模型（object oriented data model）
    - 对象关系数据模型（object relational data model）
    - 半结构化数据模型（semistructured data model）
    - ···
  - 物理模型（physical model）：描述数据在系统内部的表示方式和存取方法，或在磁盘或磁带上的存储方式和存取方法，是面向计算机系统的。

