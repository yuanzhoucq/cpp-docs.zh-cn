---
title: "错误 C1081 | Microsoft Docs"
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
  - "C1081"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1081"
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1081
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 文件名太长  
  
 文件路径名的长度超过 `_MAX_PATH`（由 STDLIB.h 定义为 260 个字符）。  缩短文件的名称。  
  
 如果用短文件名调用 CL.exe，则编译器可能需要生成完整的路径名。  例如，`cl -c myfile.cpp` 可能导致编译器生成：  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```