---
title: "CColumnAccessor 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CColumnAccessor"
  - "ATL::CColumnAccessor"
  - "ATL.CColumnAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CColumnAccessor 类"
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CColumnAccessor 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成插入了使用者代码。  
  
## 语法  
  
```  
class CColumnAccessor : public CAccessorBase  
```  
  
## 备注  
 在插入的代码，则每个列绑定作为单独访问器。  您应当知道此类在注入的代码 \(例如，可能遇到此警告，在调试\)，但是，您通常不需要直接使用或其方法。  
  
 `CColumnAccessor` 执行以下存根方法，每个对应于其他任何访问器类方法：  
  
-   `CColumnAccessor` 构造函数；实例化和初始化 `CColumnAccessor` 对象。  
  
-   `CreateAccessor`分配列绑定结构的内存并初始化列数据成员。  
  
-   对**BindColumns** 访问函数的绑定列。  
  
-   **SetParameterBuffer** 参数分配的缓冲区。  
  
-   `AddParameter`将参数输入到参数类型结构。  
  
-   确保**HasOutputColumns** 访问器是否输出列  
  
-   确保**HasParameters** 访问器是否有参数。  
  
-   `BindParameters` 绑定创建的参数中的列。  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)