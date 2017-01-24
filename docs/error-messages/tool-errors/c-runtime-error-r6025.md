---
title: "C 运行时错误 R6025 | Microsoft Docs"
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
  - "R6025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6025"
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C 运行时错误 R6025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

纯虚函数调用  
  
 没有为处理纯虚函数调用实例化任何对象。  
  
 如果应用程序出现此错误，请与该应用程序的技术支持部门联系。  
  
 导致该错误的原因是通过到派生类类型的转换所创建的指针调用抽象基类中的虚函数，而该指针实际是指向基类的指针。  在构造基类的过程中创建 **void\*** 时，将 **void\*** 转换为类指针时会发生该错误。  
  
 有关详细信息，请访问 [Microsoft 支持](http://go.microsoft.com/fwlink/?LinkId=75220)。