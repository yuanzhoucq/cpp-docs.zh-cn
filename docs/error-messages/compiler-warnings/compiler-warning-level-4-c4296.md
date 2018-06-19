---
title: 编译器警告 （等级 4） C4296 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4296
dev_langs:
- C++
helpviewer_keywords:
- C4296
ms.assetid: 9d99aafe-f6bd-4ee0-b8d0-98ce5712274d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5af2913e2c0faec16fa9b898998bfb60720cf201
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295222"
---
# <a name="compiler-warning-level-4-c4296"></a>编译器警告（等级 4）C4296
operator： 表达式始终为 false  
  
 值为零的比较操作中使用了无符号的变量。  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。  
  
 下面的示例生成 C4296:  
  
```  
// C4296.cpp  
// compile with: /W4  
#pragma warning(default : 4296)  
int main()  
{  
   unsigned int u = 9;  
   if (u < 0)    // C4296  
      u++;  
   if (u >= 0)   // C4296  
      u++;  
}  
```