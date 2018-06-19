---
title: 编译器警告 （等级 1） C4606 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4606
dev_langs:
- C++
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf9f0a954b48e2c8bd036651efa3e8a3e65b8e68
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279453"
---
# <a name="compiler-warning-level-1-c4606"></a>编译器警告（等级 1）C4606
\#杂注警告: warning_number 忽略;代码分析警告不与警告级别相关联  
  
 代码分析警告，仅`error`， `once`，和`default`支持[警告](../../preprocessor/warning.md)杂注。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4606。  
  
```  
// C4606.cpp  
// compile with: /c /W1  
#pragma warning(1: 6001)   // C4606  
#pragma warning(once: 6001)   // OK  
```