---
title: 编译器错误 C3452 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3452
dev_langs:
- C++
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: baa8470d6c7c0ffe38c6f6be07bb67a9ae932de9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249625"
---
# <a name="compiler-error-c3452"></a>编译器错误 C3452
列出不是常量的参数成员  
  
 参数被传递到一个特性，但此特性需要一个常量，即一个在编译时可计算出结果的值。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3452。  
  
```  
// C3452.cpp  
// compile with: /c  
int i;  
[module( name="mod", type=dll, custom={i} ) ];   // C3452  
// try the following line instead  
// [module( name="mod", type=dll, custom={"a"} ) ];  
```