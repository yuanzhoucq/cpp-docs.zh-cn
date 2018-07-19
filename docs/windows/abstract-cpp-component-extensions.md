---
title: 抽象 （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
dev_langs:
- C++
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dcaef98df96b54025cd44a52a2e27a7bc5a83545
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857550"
---
# <a name="abstract--c-component-extensions"></a>abstract（C++ 组件扩展）
`abstract` 关键字声明以下两者之一：  
  
-   类型可被用作基类型，但其自身无法进行实例化。  
  
-   只可在派生类型中定义类型成员函数。  
  
## <a name="all-platforms"></a>所有平台  
 **语法**  
  
```  
  
      class-declaration  
      class-identifier  
      abstract {}  
virtualreturn-typemember-function-identifier() abstract ;  
  
```  
  
 **备注**  
  
 第一个示例语法将类声明为抽象类。 *类声明*组件可以是本机 c + + 声明 (`class`或`struct`)，也可以是 c + + 扩展声明 (`ref class`或`ref struct`) 如果 **/ZW**或 **/clr**指定编译器选项。  
  
 第二个示例语法将虚拟成员函数声明为抽象函数。 将函数声明为抽象函数等同于将其声明为纯虚拟函数。 将成员函数声明为抽象函数也会导致封闭类声明为抽象类。  
  
 `abstract`关键字在本机和特定于平台的代码中受支持; 也就是说，它可以编译和不带 **/ZW**或 **/clr**编译器选项。  
  
 你可以在编译时检测类型是否为抽象与`__is_abstract(type)`类型特征。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 `abstract` 关键字是上下文相关的重写说明符。 有关上下文相关关键字的详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。 有关重写说明符的详细信息，请参阅[如何： 在本机编译中声明重写说明符](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 有关详细信息，请参阅[Ref 类和结构](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的代码示例生成一个错误，因为类 `X` 被标记为 `abstract`。  
  
```  
// abstract_keyword.cpp  
// compile with: /clr  
ref class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X ^ MyX = gcnew X;   // C3622  
}  
```  
  
 **示例**  
  
 下面的代码示例生成一个错误，因为它实例化被标记为 `abstract` 的本机类。 将出现此错误，带有或不带 **/clr**编译器选项。  
  
```  
// abstract_keyword_2.cpp  
class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'  
                    // cannot be instantiated. See declaration of 'X'}  
  
```  
  
 **示例**  
  
 下面的代码示例生成一个错误，因为函数 `f` 包含了一个定义，但被标记为 `abstract`。 示例中的最后一条语句显示声明抽象虚拟函数等效于声明纯虚拟函数。  
  
```  
// abstract_keyword_3.cpp  
// compile with: /clr  
ref class X {  
public:  
   virtual void f() abstract {}   // C3634  
   virtual void g() = 0 {}   // C3634  
};  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)