---
title: 编译器错误 C2632 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2632
dev_langs:
- C++
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3bc07c404a1f4d667045fdfea24009e7d20ad69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232628"
---
# <a name="compiler-error-c2632"></a>编译器错误 C2632
type1 跟 type2 是非法的  
  
 如果缺少两个类型说明符之间的代码，则可以导致此错误。  
  
 下面的示例生成 C2632:  
  
```  
// C2632.cpp  
int float i;   // C2632  
```  
  
 此错误还可能来自于为 Visual Studio.NET 2003年执行的编译器一致性工作。 `bool` 现在是正确的类型。 在以前版本，`bool`是的 typedef，并可以创建具有该名称的标识符。  
  
 下面的示例生成 C2632:  
  
```  
// C2632_2.cpp  
// compile with: /LD  
void f(int bool);   // C2632  
```  
  
 若要解决此错误，以使代码在 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中有效，重命名标识符。