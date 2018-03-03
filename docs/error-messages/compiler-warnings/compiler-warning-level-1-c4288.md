---
title: "编译器警告 （等级 1） C4288 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4288
dev_langs:
- C++
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a10a7573df5986ed20475b34208a1e0f301d9bb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4288"></a>编译器警告（等级 1）C4288
使用的非标准扩展: var： 在 for 循环中声明的循环控制变量用在 for 循环范围中; 外它与外层作用域中的声明冲突  
  
 使用编译时[/Ze](../../build/reference/za-ze-disable-language-extensions.md)和**/zc: forscope-**中, 声明的变量**为**之后使用循环已[为](../../cpp/for-statement-cpp.md)-循环作用域。 C + + 语言的 Microsoft 扩展允许此变量，以保持在范围内，并且 C4288 提醒您未使用的变量的第一个声明。  
  
 请参阅[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)有关如何指定中的 Microsoft 扩展**为**使用 /Ze 循环。  
  
 下面的示例生成 C4288:  
  
```  
// C4288.cpp  
// compile with: /W1 /c /Zc:forScope-  
int main() {  
   int i = 0;    // not used in this program  
   for (int i = 0 ; ; ) ;  
   i++;   // C4288 using for-loop declaration of i  
}  
```