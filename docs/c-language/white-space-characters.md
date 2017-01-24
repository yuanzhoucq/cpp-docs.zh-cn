---
title: "空白字符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字符, 空白"
  - "空白, 字符"
ms.assetid: 030ccbdc-2db3-4dd0-88c8-f5c2669ddebf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 空白字符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

空格、制表符、换行符、回车符、换页符、垂直制表符和换行符称为“空白字符”，因为它们与打印页上的单词和行之间的空格一样都是起到方便阅读的作用。  标记由空白字符和其他标记分隔（划分边界），如运算符和标点。  在分析代码时，C 编译器将忽略空白字符，除非您将它们用作分隔符或者字符常量或字符串文本的组成部分。  使用空白字符可以让程序更易于阅读。  请注意，编译器也将注释视为空白。  
  
## 请参阅  
 [C 标记](../c-language/c-tokens.md)