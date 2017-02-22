---
title: "CRowset::Insert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CRowset<TAccessor>.Insert"
  - "CRowset.Insert"
  - "CRowset<TAccessor>.Insert"
  - "CRowset<TAccessor>::Insert"
  - "ATL::CRowset<TAccessor>::Insert"
  - "ATL.CRowset.Insert"
  - "CRowset::Insert"
  - "ATL::CRowset::Insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Insert 方法"
ms.assetid: 6a64a1c3-10ac-4296-8685-0fd6fe63a13b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CRowset::Insert
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CRowset::Insert 使用访问器中的数据创建并初始化新行。  
  
## 语法  
  
```  
  
      HRESULT Insert(   
   int nAccessor = 0,   
   bool bGetHRow = false    
) throw( );  
```  
  
#### 参数  
 `nAccessor`  
 \[in\] 用来插入数据的访问器的索引号  
  
 *bGetHRow*  
 \[in\] 指示插入的行句柄是否检索。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法要求可选接口 `IRowsetChange`，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  还必须设置**DBPROP\_IRowsetChange**为`VARIANT_TRUE` 在对包含行集合中的 **打开** 表或命令。  
  
 如果一个或多个列是不可写的，则插入操作可能会失败。  修改游标映射以更正此问题。  
  
## 示例  
 使用该行集合的表，下面的示例演示如何遍历数据行集访问源然后插入字符串。  
  
 首先，通过插入新的 ATL 对象创建表类到项目。  例如，右击在工作区窗格的项目并选择 **New ATL Object**。  从 **Data Access** 类，选择 **使用者**。  创建 **表**类型使用者对象。\(选择 **表** 创建一行集直接从表；选择 **命令** 通过 SQL 命令创建该行集合。\)选择指定一表访问数据源，该数据源。  如果使用者对象调用 **CCustomerTable**，然后实现插入如下代码：  
  
 [!code-cpp[NVC_OLEDB_Consumer#10](../../data/oledb/codesnippet/CPP/crowset-insert_1.cpp)]  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)