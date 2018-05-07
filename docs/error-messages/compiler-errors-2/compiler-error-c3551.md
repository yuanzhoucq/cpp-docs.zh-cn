---
title: 编译器错误 C3551 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3551
dev_langs:
- C++
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f9f69adcf071415d3c1760294bdaaaec7b71f8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3551"></a>编译器错误 C3551
“应为后期指定的返回类型”  
  
 如果你使用 `auto` 关键字作为函数返回类型的占位符，必须提供后指定返回类型。 在下面的示例中，函数 `myFunction` 的后期指定返回类型是一个指针，该指针指向由四个 `int`类型的元素组成的数组。  
  
```  
auto myFunction()->int(*)[4];   
```  
  
## <a name="see-also"></a>请参阅  
 [auto](../../cpp/auto-cpp.md)