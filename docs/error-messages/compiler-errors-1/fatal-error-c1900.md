---
title: "错误 C1900 | Microsoft Docs"
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
  - "C1900"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1900"
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1900
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“tool1”版本“number1”和“tool2”版本“number2”之间的 IL 不匹配  
  
 编译器的各种 pass 中运行的工具不匹配。  ***number1*** 和 ***number2*** 是指文件上的日期。  例如，在 pass 1 中，编译器前端运行 \(c1.dll\)，而在 pass 2 中，编译器后端运行 \(c2.dll\)。  文件上的日期必须匹配。  
  
 若要解决此问题，请确保 Visual Studio 已应用所有的更新。  如果问题仍然存在，请使用 Windows 控制面板中的“程序和功能”修复或重新安装 Visual Studio。