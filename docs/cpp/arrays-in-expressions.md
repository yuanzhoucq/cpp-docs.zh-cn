---
title: "表达式中的数组 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], 在表达式中"
  - "表达式 [C++], 数组"
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 表达式中的数组
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当数组类型的标识符出现在 `sizeof`、address\-of \(**&**\) 或引用的初始化以外的表达式中时，该标识符将转换为指向第一个数组元素的指针。  例如：  
  
```  
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 指针 `psz` 指向数组 `szError1` 的第一个元素。  请注意，与指针不同，数组不是可修改的左值。  因此，以下赋值是非法的：  
  
```  
szError1 = psz;  
```  
  
## 请参阅  
 [数组](../cpp/arrays-cpp.md)