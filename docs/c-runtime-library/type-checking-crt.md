---
title: "类型检查 (CRT) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.types
dev_langs:
- C++
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d18ae0818dd839bee0d93bd7194dadcc9abf6627
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="type-checking-crt"></a>类型检查 (CRT)
编译器对可采用可变数目的自变量的函数执行有限类型检查，如下所示：  
  
|函数调用 |类型检查的参数|  
|-------------------|-----------------------------|  
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|第一个参数（格式字符串）|  
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|前两个自变量（文件或缓冲区和格式字符串）|  
|`_snprintf_s`|前三个自变量（文件或缓冲区、计数和格式字符串）|  
|`_open`|前两个参数（路径和 `_open` 标志）|  
|`_sopen_s`|前三个参数（路径、`_open` 标志和共享模式）|  
|`_execl`, `_execle`, `_execlp`, `_execlpe`|前两个参数（路径和第一个参数指针）|  
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|前三个参数（模式标志、路径和第一个参数指针）|  
  
 编译器会对这些函数的宽字符对等执行相同的有限类型检查。  
  
## <a name="see-also"></a>请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)