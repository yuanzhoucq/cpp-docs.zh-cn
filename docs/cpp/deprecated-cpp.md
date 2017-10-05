---
title: "弃用 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- deprecated
- deprecated_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 9ac25648e2d19da82f6c213992699c237e05c01e
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="deprecated-c"></a>已弃用 (C++)
本主题只介绍特定于 Microsoft 的弃用 declspec 声明。 有关 C + + 14`[[deprecated]]`属性，以及有关何时使用与 Microsoft 专用 declspec 或杂注时，该属性的指导，请参阅[c + + 标准特性](attributes2.md)。

 与所示的异常**弃用**声明提供与相同的功能[弃用](../preprocessor/deprecated-c-cpp.md)杂注：  
  
-   **弃用**声明允许你的函数重载的特殊形式指定为已弃用，而杂注形式适用于所有重载形式的函数名称。  
  
-   **弃用**声明允许您指定在编译时将显示一条消息。 该消息的文本可以来自宏。  
  
-   宏仅被标记为已弃用，**弃用**杂注。  
  
 如果编译器遇到不推荐使用的标识符或标准使用[ `[[deprecated]]` ](attributes2.md)属性， [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)引发警告。  
  
## <a name="example"></a>示例  
 下面的示例演示在使用已弃用的函数时，如何将函数标记为已弃用以及如何指定在编译时将显示的消息。  
  
```  
// deprecated.cpp  
// compile with: /W3  
#define MY_TEXT "function is deprecated"  
void func1(void) {}  
__declspec(deprecated) void func1(int) {}  
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}  
__declspec(deprecated(MY_TEXT)) void func3(int) {}  
  
int main() {  
   func1();  
   func1(1);   // C4996  
   func2(1);   // C4996  
   func3(1);   // C4996  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例演示在使用已弃用的类时，如何将类标记为已弃用以及如何指定在编译时将显示的消息。  
  
```  
// deprecate_class.cpp  
// compile with: /W3  
struct __declspec(deprecated) X {  
   void f(){}  
};  
  
struct __declspec(deprecated("** X2 is deprecated **")) X2 {  
   void f(){}  
};  
  
int main() {  
   X x;   // C4996  
   X2 x2;   // C4996  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)
