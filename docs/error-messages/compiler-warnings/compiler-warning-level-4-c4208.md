---
title: 编译器警告 （等级 4） C4208 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4208
dev_langs:
- C++
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b61f8b0a6a0ac61982bee79abb81f083d40a48f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292358"
---
# <a name="compiler-warning-level-4-c4208"></a>编译器警告（等级 4）C4208
使用的非标准扩展： 删除 [exp]-exp 计算但忽略  
  
 具有 Microsoft 扩展 (/Ze)，你可以删除数组使用括号内的某个值[delete 运算符](../../cpp/delete-operator-cpp.md)。 忽略的值。  
  
```  
// C4208.cpp  
// compile with: /W4  
int main()  
{  
   int * MyArray = new int[18];  
   delete [18] MyArray;      // C4208  
   MyArray = new int[18];  
   delete [] MyArray;        // ok  
}  
```  
  
 此类值均无效 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。