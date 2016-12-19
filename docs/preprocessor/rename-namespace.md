---
title: "rename_namespace | Microsoft Docs"
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
  - "rename_namespace"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "rename_namespace 特性"
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rename_namespace
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 重命名包含类型库内容的命名空间。  
  
## 语法  
  
```  
rename_namespace("NewName")  
```  
  
#### 参数  
 `NewName`  
 命名空间的新名称。  
  
## 备注  
 它采用单个参数 *NewName*，用来为命名空间指定新名称。  
  
 若要删除命名空间，请改用 [no\_namespace](../preprocessor/no-namespace.md) 特性。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)