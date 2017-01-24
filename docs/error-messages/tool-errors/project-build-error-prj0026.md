---
title: "项目生成错误 PRJ0026 | Microsoft Docs"
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
  - "PRJ0026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0026"
ms.assetid: c52bc9b5-8b22-4015-b477-8645ae56c489
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

响应文件“file”包含未能翻译成用户 ANSI 代码页的 Unicode 内容。  
  
 ***文件的 UNICODE 内容***  
  
 项目系统在响应文件中发现了不能翻译成用户的当前 ANSI 代码页的 Unicode 内容。  
  
 该错误的解决方法是更新响应文件的内容以使用 ANSI，或在计算机上安装代码页并将其设置为系统的默认代码页。