---
title: "文本 （c + + 组件扩展） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- literal
- literal_cpp
dev_langs: C++
helpviewer_keywords: literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d13c8b081f3bcc3efbf20be3c31e2601baa6ca02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="literal-c-component-extensions"></a>文本（C++ 组件扩展）
（数据成员） 的变量标记为`literal`中**/clr**编译为等同的本机`static const`变量。  
  
## <a name="all-platforms"></a>所有平台  
 **备注**  
  
 （此语言功能没有适用于所有运行时的备注。）  
  
## <a name="windows-runtime"></a>Windows 运行时  
 **备注**  
  
 (此语言功能没有只适用于 Windows 运行时的备注。）  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时  
  
## <a name="remarks"></a>备注  
 数据成员标记为`literal`声明时必须初始化和值必须为常量整型、 枚举类型或字符串类型。 从初始化表达式类型转换为静态常量数据成员类型时，不能使用用户定义的转换。  
  
 没有在运行时为文本字段分配内存；编译器只将其值插入该类的元数据中。  
  
 元数据中标记为 `static const` 的变量不可用于其他编译器。  
  
 有关详细信息，请参阅[静态](../cpp/storage-classes-cpp.md)和[const](../cpp/const-cpp.md)。  
  
 `literal` 是上下文相关的关键字。 请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)有关详细信息。  
  
## <a name="example"></a>示例  
 此示例显示，`literal` 变量表示 `static`。  
  
```  
// mcppv2_literal.cpp  
// compile with: /clr  
ref struct X {  
   literal int i = 4;  
};  
  
int main() {  
   int value = X::i;  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例演示了对元数据的文本影响：  
  
```  
// mcppv2_literal2.cpp  
// compile with: /clr /LD  
public ref struct A {  
   literal int lit = 0;  
   static const int sc = 1;  
};  
```  
  
 注意 `sc` 和 `lit` 在元数据上的区别：`modopt` 指令应用于 `sc`，表示其他编译器会将其忽略。  
  
```  
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)  
```  
  
```  
.field public static literal int32 lit = int32(0x0000000A)  
```  
  
## <a name="example"></a>示例  
 下面的示例使用 C# 编写，引用上一示例中创建的元数据并显示 `literal` 和 `static const` 变量的影响：  
  
```  
// mcppv2_literal3.cs  
// compile with: /reference:mcppv2_literal2.dll  
// A C# program  
class B {  
   public static void Main() {  
      // OK  
      System.Console.WriteLine(A.lit);  
      System.Console.WriteLine(A.sc);  
  
      // C# does not enforce C++ const  
      A.sc = 9;  
      System.Console.WriteLine(A.sc);  
  
      // C# enforces const for a literal  
      A.lit = 9;   // CS0131  
  
      // you can assign a C++ literal variable to a C# const variable  
      const int i = A.lit;  
      System.Console.WriteLine(i);  
  
      // but you cannot assign a C++ static const variable  
      // to a C# const variable  
      const int j = A.sc;   // CS0133  
      System.Console.WriteLine(j);  
   }  
}  
```  
  
## <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
## <a name="see-also"></a>另请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)