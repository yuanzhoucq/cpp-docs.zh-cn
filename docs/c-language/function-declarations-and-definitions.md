---
title: "函数声明和定义 | Microsoft Docs"
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
  - "声明函数"
  - "声明函数, 函数定义"
  - "外部声明"
  - "外部链接, 函数声明"
  - "函数定义, 函数声明"
  - "函数原型, 基本知识"
  - "内部声明"
  - "本地声明"
ms.assetid: 43fd98eb-7441-4473-a5d9-fc88c75577f7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函数声明和定义
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

函数原型确定了函数的名称、返回类型以及形参的类型和数量。  函数定义包括函数体。  
  
## 备注  
 函数声明和变量声明均可出现在函数定义的内部或外部。  函数定义中的所有声明应在“内部”或“局部”级别显示。  所有函数定义之外的声明应在“外部”、“全局”或“文件范围”级别显示。  变量定义（如声明）可在内部级别（在函数定义中）或在外部级别（在所有函数定义外）显示。  函数定义始终会在外部级别显示。  [函数定义](../c-language/c-function-definitions.md)中进一步讨论了函数定义。  [函数原型](../c-language/function-prototypes.md)中介绍了函数原型。  
  
## 请参阅  
 [源文件和源程序](../c-language/source-files-and-source-programs.md)