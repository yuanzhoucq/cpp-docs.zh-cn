---
title: "资源编译器错误 RC2148 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2148"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2148"
ms.assetid: 0290065c-35d3-4815-80c5-40bf7132ae1d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 资源编译器错误 RC2148
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

SUBLANGUAGE ID 太大  
  
 SUBLANGUAGE ID 值超出了范围。  
  
 **LANGUAGE** 语句必须使用以下语法：  
  
 **LANGUAGE** *primary\_language\_ID*,*secondary\_language\_ID*  
  
 有效的 SUBLANGUAGE ID 被定义为 WINNT.h 文件中的 **SUBLANG\_** 常数。