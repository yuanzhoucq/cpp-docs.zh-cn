---
title: 编译器错误 C3554 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3554
dev_langs:
- C++
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fb374e028097157ae72b621593a899af9fe2f91
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3554"></a>编译器错误 C3554
“decltype”不能与任何其他类型说明符组合  
  
 不可用任何类型说明符来限定 `decltype()` 关键字。 例如，下述代码片段产生错误 C3554。  
  
```  
int x;  
unsigned decltype(x); // C3554  
```