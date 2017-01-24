---
title: "no_registry | Microsoft Docs"
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
  - "no_registry"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "no_registry 特性"
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# no_registry
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`no_registry` 告知编译器不在寄存器中搜索使用 `#import` 导入的类型库。  
  
## 语法  
  
```  
  
#import filename no_registry  
```  
  
#### 参数  
 *filename*  
 类型库。  
  
## 备注  
 如果未在包括目录中找到引用类型库，则编译将失败，即使该类型库位于寄存器中也是如此。`no_registry` 将传播到使用 `auto_search` 隐式导入的其他类型库。  
  
 编译器绝不会在寄存器中搜索由文件名指定并直接传递到 `#import` 的类型库。  
  
 指定 `auto_search` 后，将使用初始 `#import` 的 `no_registry` 设置生成额外的 `#import`（如果初始 `#import` 指令是 `no_registry`，则 `auto_search` 生成的 `#import` 也是 `no_registry`。）  
  
 如果您希望跨引用类型库导入时没有编译器在寄存器中发现文件的早期版本的风险，则 `no_registry` 很有用。如果未注册类型库，则 `no_registry` 也很有用。  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)