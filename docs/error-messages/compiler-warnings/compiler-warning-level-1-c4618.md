---
title: 编译器警告 （等级 1） C4618 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4618
dev_langs:
- C++
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e53f8542983a6e15f353ff181efa280815fea9d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282517"
---
# <a name="compiler-warning-level-1-c4618"></a>编译器警告（等级 1）C4618
杂注参数包含一个空字符串;忽略杂注  
  
 一个 null 字符串形式的自变量提供 **#pragma**。  
  
 处理杂注，而不使用参数。  
  
 下面的示例生成 C4618:  
  
```  
// C4618.cpp  
// compile with: /W1 /LD  
#pragma code_seg("")   // C4618  
```