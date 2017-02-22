---
title: "项目生成错误 PRJ0027 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0027"
ms.assetid: 85d73a78-4b9e-4553-9f5d-2d76c48a790a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 项目生成错误 PRJ0027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Unicode 日志消息“contents”包含未能翻译成用户的 ANSI 代码页的内容。  
  
 通常只有在创建批处理文件和\/或响应文件时出错时才会看到该警告。  
  
 该错误的解决方法是更新生成日志的内容以使用 ANSI，或在计算机上安装代码页并将其设置为系统的默认代码页。