---
title: "类型检查 (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "检查类型"
  - "类型检查"
  - "变量参数函数"
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 类型检查 (CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

编译器可能对可采用可变数量的实函数的有限类型检查，例如：  
  
|函数调用|检查类型的参数|  
|----------|-------------|  
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|第一个参数 \(字符串格式\)|  
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|前两个参数 \(文件或缓冲区和格式字符串\)|  
|`_snprintf_s`|前三参数 \(文件或缓冲区、计数和格式字符串\)|  
|`_open`|前两个参数 \(和 `_open` 标志\) 路径|  
|`_sopen_s`|前三参数 \(路径、`_open` 和 Shared 模式\)|  
|`_execl`, `_execle`, `_execlp`, `_execlpe`|前两个参数 \(第一个参数\) 指针和路径|  
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|前三参数模式 \(标志、路径和第一个形指针\)|  
  
 编译器对这些函数宽字符副本的相同限制类型检查。  
  
## 请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)