---
title: "__uuidof 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__LIBID_"
  - "__LIBID_cpp"
  - "__uuidof"
  - "__uuidof_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__LIBID_ 关键字 [C++]"
  - "__uuidof 关键字 [C++]"
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# __uuidof 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 检索 GUID 并附加到表达式。  
  
## 语法  
  
```  
  
      __uuidof (  
   expression   
)  
```  
  
## 备注  
 该 *表达式* 可以是类型名称、指针、引用或该类型的数组、特定类型的模板或这些类型的变量。  只要编译器可以使用它查找附加的 GUID，自变量就是有效的。  
  
 内部函数的一个特例就是当在 **0** 或 **NULL** 中作为参数提供。  在这种情况下，`__uuidof` 将返回由零组成的GUID。  
  
 使用此关键字用以提取附加的 GUID:  
  
-   一个对象通过 [uuid](../cpp/uuid-cpp.md) 扩展其特性。  
  
-   库块以使用 [模块](../windows/module-cpp.md) 属性创建。  
  
> [!NOTE]
>  在调试版本中，`__uuidof` 总是动态初始化一个对象 \(运行时\)。  当发布版本时，`__uuidof` 可以静态初始化对象（在编译时）。  
  
## 示例  
 下面的代码 \(使用ole32.lib编译\) 将显示一个创建模块属性库块uuid：  
  
```  
// expre_uuidof.cpp  
// compile with: ole32.lib  
#include "stdio.h"  
#include "windows.h"  
  
[emitidl];  
[module(name="MyLib")];  
[export]  
struct stuff {  
   int i;  
};  
  
int main() {  
   LPOLESTR lpolestr;  
   StringFromCLSID(__uuidof(MyLib), &lpolestr);  
   wprintf_s(L"%s", lpolestr);  
   CoTaskMemFree(lpolestr);  
}  
```  
  
## 注释  
 当库名不再在范围之内，你可以使用\_\_LIBID\_而不是 `__uuidof`。  例如：  
  
```  
StringFromCLSID(__LIBID_, &lpolestr);  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)