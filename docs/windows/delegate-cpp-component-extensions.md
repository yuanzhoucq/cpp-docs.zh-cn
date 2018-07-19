---
title: 委托 （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
dev_langs:
- C++
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 73d40bb33509f89273b37f7704cd1922a8d5adc2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879654"
---
# <a name="delegate--c-component-extensions"></a>委托（C++ 组件扩展）
声明表示函数指针的类型。  
  
## <a name="all-runtimes"></a>所有运行时  
 Windows 运行时和公共语言运行时支持委托。  
  
### <a name="remarks"></a>备注  
 `delegate` 是上下文相关的关键字。 有关详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
 若要在编译时检测类型是否为委托，使用`__is_delegate()`类型特征。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 C + + /cli CX 支持使用以下语法的委托。  
  
### <a name="syntax"></a>语法  
  
```cpp  
access  
delegate  
return-type  
delegate-type-identifier  
(  
[ parameters ]  
)  
  
```  
  
### <a name="parameters"></a>参数  
 *access*  
 （可选）委托，委托可以是可访问性`public`（默认值） 或`private`。 函数原型也可以限定与`const`或`volatile`关键字。  
  
 *返回类型*  
 函数原型返回类型。  
  
 *委托类型标识符*  
 声明的委托类型的名称。  
  
 *参数*  
 （可选）类型和函数原型的标识符。  
  
### <a name="remarks"></a>备注  
 使用*委托类型标识符*声明具有相同的原型作为委派的事件。 有关详细信息，请参阅[委托 (C + + /cli CX)](../cppcx/delegates-c-cx.md)。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时  
 公共语言运行时支持使用以下语法的委托。  
  
### <a name="syntax"></a>语法  
  
```cpp  
access  
delegate  
function_declaration  
  
```  
  
### <a name="parameters"></a>参数  
 *access*  
 （可选）在程序集之外的可访问性可以是委托的公共或私有。  默认值是私有的。  在类中，委托可以有任何可访问性。  
  
 *function_declaration*  
 可以绑定到委托的函数签名。 委托的返回类型可以是任何托管的类型。 互操作性原因，建议的委托的返回类型是符合 CLS 类型。  
  
 若要定义一个未绑定的委托中的第一个参数*function_declaration*的类型应该`this`对象的指针。 
  
### <a name="remarks"></a>备注  
 委托是多路广播:"函数指针"可以绑定到托管类中的一个或多个方法。 **委托**关键字定义了具有特定的方法签名的多路广播的委托类型。  
  
 此外可以将委托绑定到值类，如的静态方法的方法。  
  
 委托具有以下特征：  
  
-   它继承自**system:: multicastdelegate**。  
  
-   它具有一个采用两个参数的构造函数： 指向托管类的指针或**NULL** （如果要绑定到静态方法） 和指定类型的完全限定的方法。  
  
-   它具有一个称为 `Invoke` 的方法，其签名与委托的声明签名匹配。  
  
 调用委托时，将它们连接的顺序调用其功能。  
  
 委托的返回值是从其最后一个附加的成员函数的返回值。  
  
 委托不能重载。  
  
 可以绑定或未绑定的委托。  
  
 当实例化绑定的委托时，第一个参数应是一个对象引用。  委托实例化第二个参数应是值类型的方法是托管的类对象或指针的方法的地址。   委托实例化第二个参数必须命名具有完整类范围语法的方法，并应用 address-of 运算符。  
  
 当实例化未绑定的委托时，第一个参数应是方法的托管的类对象或指向值类型的方法的地址。   自变量必须命名具有完整类范围语法的方法，并应用 address-of 运算符。  
  
 在创建指向静态或全局函数的委托时，只有一个参数是必需： 函数 （（可选） 的函数的地址）。  
  
 有关委托的更多信息，请参阅  
  
-   [如何：定义和使用委托 (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)  
  
-   [泛型委托 (Visual C++)](../windows/generic-delegates-visual-cpp.md)  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的示例演示如何声明、 初始化和调用委托。  
  
```cpp  
// mcppv2_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare a delegate  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      Console::WriteLine("in func1 {0}", i);  
   }  
  
   void func2(int i) {  
      Console::WriteLine("in func2 {0}", i);  
   }  
  
   static void func3(int i) {  
      Console::WriteLine("in static func3 {0}", i);  
   }  
};  
  
int main () {  
   A ^ a = gcnew A;  
  
   // declare a delegate instance  
   MyDel^ DelInst;  
  
   // test if delegate is initialized  
   if (DelInst)  
      DelInst(7);  
  
   // assigning to delegate  
   DelInst = gcnew MyDel(a, &A::func1);  
  
   // invoke delegate  
   if (DelInst)  
      DelInst(8);  
  
   // add a function  
   DelInst += gcnew MyDel(a, &A::func2);  
  
   DelInst(9);  
  
   // remove a function  
   DelInst -= gcnew MyDel(a, &A::func1);  
  
   // invoke delegate with Invoke  
   DelInst->Invoke(10);  
  
   // make delegate to static function  
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);  
   StaticDelInst(11);  
}  
```  
  
 **输出**  
  
```Output  
in func1 8  
  
in func1 9  
  
in func2 9  
  
in func2 10  
  
in static func3 11  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)