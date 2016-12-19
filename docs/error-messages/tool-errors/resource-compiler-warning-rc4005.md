---
title: "资源编译器警告 RC4005 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC4005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4005"
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器警告 RC4005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 宏重定义  
  
 标识符被定义两次。  编译器使用了第二个宏定义。  
  
 在命令行上和带有 `#define` 指令的代码中定义宏可导致该警告。  从包含文件导入的宏也可导致该警告。  
  
 若要消除该警告，移除一个定义或者在第二个定义之前使用 `#undef` 指令。