---
title: "错误 C1047 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1047"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1047"
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1047
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对象或库文件“file”是使用比创建其他对象所用编译器旧的编译器创建的；请重新生成旧的对象和库  
  
 当使用 **\/LTCG** 生成的对象文件或库链接在一起，而这些对象文件或库是用不同版本的 Visual C\+\+ 工具集生成的，则会导致 C1047。  
  
 当你开始使用新版本的编译器，而不完全重新生成现有对象文件或库时，可能出现这种情况。  
  
 若要解决 C1047，请重新生成所有对象文件或库。