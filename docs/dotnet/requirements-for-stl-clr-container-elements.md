---
title: "STL/CLR 容器元素的要求 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "容器, STL"
  - "容器, STL/CLR"
  - "标准 C++ 库, 模板类容器"
  - "STL/CLR, 容器"
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# STL/CLR 容器元素的要求
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

插入 STL\/CLR 容器的任何引用，类型必须具有至少，以下元素：  
  
-   公共复制构造函数。  
  
-   公共赋值运算符。  
  
-   公共析构函数。  
  
 此外，与容器 \(如 [set](../dotnet/set-stl-clr.md) 和 [映射](../dotnet/map-stl-clr.md) 必须具有公共的比较运算符定义，默认为 `operator<`。  容器中的某些操作可能还需要公共默认构造函数和公共等效运算符。  
  
 与引用类型中，值类型和句柄将插入一个容器关联的类型必须有一等比较运算符定义 `operator<`。  公共复制构造函数和赋值运算符、公共公共析构函数的要求为值类型或句柄不存在引用类型。  
  
## 请参阅  
 [标准模板库](../misc/standard-template-library.md)