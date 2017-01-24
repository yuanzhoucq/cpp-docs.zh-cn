---
title: "错误 C1001 | Microsoft Docs"
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
  - "C1001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1001"
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

内部编译器错误\(编译器文件 file，行号\)  
  
 编译器无法生成正确的构造代码，原因可能是出自表达式与优化选项的组合。  尝试移除一个或多个优化选项，并重新编译包含错误消息所指示的行的函数。  
  
 通过移除一个或多个优化选项有可能解决该问题。  若要确定哪一个选项出了问题，请一次移除一个选项并重新编译，直到错误消息消失为止。  通常最有可能导致此错误的选项有 **\/Og**、**\/Oi** 和 `/Oa`。  确定了哪一个选项是症结所在后，则可以对发生错误的函数使用 [optimize](../../preprocessor/optimize.md) 杂注来禁用它，并为模块的其余部分继续使用该选项。  
  
 Microsoft知识库含有有关 C1001 的更多信息，请参见see [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;134650](http://support.microsoft.com/default.aspx?scid=kb;en-us;134650).  
  
 尝试重写报告错误的行或围绕该行周围的若干行。