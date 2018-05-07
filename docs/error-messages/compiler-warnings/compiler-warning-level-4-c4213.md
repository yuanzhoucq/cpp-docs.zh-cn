---
title: 编译器警告 （等级 4） C4213 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4213
dev_langs:
- C++
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 407fac636ea33c8cbd31104460442e5ac2aaec65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4213"></a>编译器警告（等级 4）C4213
使用的非标准扩展： 上左值的类型转换  
  
 具有默认的 Microsoft 扩展 (/Ze) 中，可以在赋值语句的左侧使用强制转换。  
  
## <a name="example"></a>示例  
  
```  
// C4213.c  
// compile with: /W4  
void *a;  
void f()  
{  
   int   i[3];  
   a = &i;  
   *(( int * )a )++ = 3;  // C4213  
}  
  
int main()  
{  
}  
```  
  
 此类强制转换时在 ANSI 兼容性无效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。