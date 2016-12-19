---
title: "读取范围 | Microsoft Docs"
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
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 读取范围
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.9.6.2** 短划线 \(–\) 字符的解释，该字符既不是 `fscanf` 函数的 % \[ 转换的扫描表中的第一个字符，也不是该表中的最后一个字符  
  
 下面的行  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 将 A \- Z 范围内的任意数目的字符读取到 `strptr` 指向的字符串中。  
  
## 请参阅  
 [库函数](../c-language/library-functions.md)