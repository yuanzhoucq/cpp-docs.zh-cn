---
title: "编译器错误 C3861 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3861
dev_langs:
- C++
helpviewer_keywords:
- C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
caps.latest.revision: 10
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
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 177890dcd3ff2abf07f5d9e282efd4a9fd7121a7
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3861"></a>编译器错误 C3861
“identifier”：找不到标识符  
  
即使使用自变量相关的查找，编译器也无法解析对标识符的引用。  
  
要修复此错误，请检查标识符声明的大小写和拼写。 验证[划分在作用域解析运算符](../../cpp/scope-resolution-operator.md)和命名空间[using 指令](../../cpp/namespaces-cpp.md#using_directives)正确使用。 如果该标识符是在头文件中声明的，请确保在引用之前已包含该头文件。 此外检查该标识符不排除了[条件编译指令](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。  
  
## <a name="example"></a>示例  
下面的示例生成 C3861。  
  
```cpp  
// C3861.cpp  
void f2(){}  
int main() {  
   f();   // C3861  
   f2();   // OK  
}  
```  
  
## <a name="example"></a>示例  
C++ 标准库中的异常类现在位于 `std` 命名空间中。  
  
```cpp  
// C3861_b.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   try {  
      throw exception("Exception");   // C3861  
      // try the following line instead  
      // throw std::exception("Exception");  
   }  
   catch (...) {  
      std::cout << "caught an exception" << std::endl;  
   }  
}  
```
