---
title: 错误 C1091 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1091
dev_langs:
- C++
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c48c9dca72bddc844e94fb7978cb6414aa8fecf5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1091"></a>错误 C1091
编译器限制：字符串长度超过“length”个字节  
  
 字符串常量超过当前的字符串长度限制。  
  
 你可能希望将静态字符串拆分为两个（或更多）变量，以及使用 [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 在声明或在运行时联接结果。