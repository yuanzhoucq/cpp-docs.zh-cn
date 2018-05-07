---
title: 错误 C1094 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1094
dev_langs:
- C++
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e227cbfaf46eb7616ae63eda02816e7d274ab85b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1094"></a>错误 C1094
-Zmval1： 命令行选项是与用于生成预编译标头的值不一致 (-Zmval2)  
  
 传递到值[/Yc](../../build/reference/yc-create-precompiled-header-file.md)必须是相同的值传递给[/Yu](../../build/reference/yu-use-precompiled-header-file.md) (**/Zm**值必须在所有编译中，使用或创建相同的预编译相同标头文件）。  
  
 下面的示例生成 C1094:  
  
```  
// C1094.h  
int func1();  
```  
  
 然后，  
  
```  
// C1094.cpp  
// compile with: /Yc"C1094.h" /Zm200  
int u;  
int main() {  
   int sd = 32;  
}  
#include "C1094.h"  
```  
  
 然后，  
  
```  
// C1094b.cpp  
// compile with: /Yu"C1094.h" /Zm300 /c  
#include "C1094.h"   // C1094 compile with /Zm200  
void Test() {}  
```