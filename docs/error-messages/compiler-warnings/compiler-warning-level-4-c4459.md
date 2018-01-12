---
title: "编译器警告 （等级 4） C4459 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4459
dev_langs: C++
helpviewer_keywords: C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 47380915dd18387fa3cc2af54d42a3777aab3f5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4459"></a>编译器警告 （等级 4） C4459
  
> 声明*标识符*隐藏了全局声明
  
声明*标识符*在本地作用域中隐藏具有相同名称的声明*标识符*在全局范围内。 此警告，告知你引用到*标识符*此作用域中解析为本地声明版本，而非全局版本，可能会也可能不是你的意图。 通常情况下，我们建议你尽量少使用的全局变量作为良好工程做法。 为了尽量减少污染全局命名空间，我们建议使用命名的命名空间的全局变量。  
  
在 Visual Studio 2015 中，在 Visual c + + 编译器版本 18.00 新此警告。 若要禁止显示该版本的编译器或更高版本时迁移你的代码的警告，请使用[/Wv:18](../../build/reference/compiler-option-warning-level.md)编译器选项。 

## <a name="example"></a>示例
  
 下面的示例生成 C4459:  
  
```cpp  
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() { 
    int global_or_local; // warning C4459 
    global_or_local = 2;
} 
```  
  
若要解决此问题的一种方法是创建您全局函数的命名空间，但不是使用`using`指令置于该命名空间的范围内，因此所有引用都必须都使用明确限定名：  
  
```cpp  
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() { 
    int global_or_local; // OK 
    global_or_local = 2;
    globals::global_or_local = 3;
} 
```  
