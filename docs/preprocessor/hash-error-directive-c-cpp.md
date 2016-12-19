---
title: "#error 指令 (C/C++) | Microsoft Docs"
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
  - "#error"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#error 指令"
  - "error 指令（#error 指令）"
  - "预处理器, 指令"
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #error 指令 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`#error` 指令在编译时发出用户指定的错误消息然后终止编译。  
  
## 语法  
  
```  
#error token-string  
```  
  
## 备注  
 此指令发出的错误消息包含 *token\-string* 参数。  `token-string` 参数不遵循宏展开。  此指令在处理向该开发人员通知项目不一致和约束冲突时最有用。  以下示例演示预处理过程中的错误进程：  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## 请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)