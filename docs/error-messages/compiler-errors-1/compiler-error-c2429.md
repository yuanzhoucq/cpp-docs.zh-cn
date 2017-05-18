---
title: "编译器错误 C2429 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2429
dev_langs:
- C++
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: eb0c1bf407d1478451c246cf615d031ef6c45bf9
ms.openlocfilehash: 7d2c27ccdba28720596984c46c9d24f9d29c7b15
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2429"></a>编译器错误 C2429
*语言功能*要求编译器标志*编译器选项*  
  
语言功能要求支持特定的编译器选项。  
  
错误 C2429: 嵌套的命名空间的定义的语言功能要求编译器标志 ' / std:c + + 中最新如果您尝试定义，则生成*复合命名空间*，包含一个或多个自 Visual Studio 2015 Update 3 起的作用域嵌套命名空间名称的命名空间。 复合命名空间定义中不允许有 c + + 在 C + +&17; 之前。 编译器支持复合命名空间定义当[/std:c + + 中最新](../../build/reference/std-specify-language-standard-version.md)指定编译器选项︰  
```cpp  
// C2429a.cpp  
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.  
                          // Use /std:c++latest to fix, or do this:  
// namespace a { namespace b { int i; }}  
  
int main() {  
   a::b::i = 2;  
}  
```  
