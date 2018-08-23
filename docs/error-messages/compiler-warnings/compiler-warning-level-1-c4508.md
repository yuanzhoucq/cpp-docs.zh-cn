---
title: 编译器警告 （等级 1） C4508 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4508
dev_langs:
- C++
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53f152c2f3573e5f3bd7b8e9be0603ed6d3f11bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283191"
---
# <a name="compiler-warning-level-1-c4508"></a>编译器警告（等级 1）C4508
function： 函数应返回一个值; 如果void 返回类型假定  
  
 函数具有指定没有返回类型。 在这种情况下，也应激发 C4430 和编译器实现的 C4430 （默认值为 int） 报告的修复。  
  
 若要解决此警告，显式声明函数的返回的类型。  
  
 下面的示例生成 C4508:  
  
```  
// C4508.cpp  
// compile with: /W1 /c  
#pragma warning (disable : 4430)  
func() {}   // C4508  
void func2() {}   // OK  
```