---
title: 委托 （c + + 组件扩展） |Microsoft Docs
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
ms.openlocfilehash: dd35674b61e61eead6118fdcc0aacccbafa6f3b4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649502"
---
# <a name="delegate--c-component-extensions"></a>委托（C++ 组件扩展）
声明表示的函数指针的类型。  
  
## <a name="all-runtimes"></a>所有运行时  
 Windows 运行时和公共语言运行时支持委托。  
  
### <a name="remarks"></a>备注  
 **委托**是上下文相关关键字。 有关详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
 若要在编译时检测类型是否为委托，使用`__is_delegate()`类型特征。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 C + + /CX 支持具有以下语法的委托。  
  
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
 （可选）委托，它可以是可访问性**公共**（默认值） 或**专用**。 此外可使用限定的函数原型**const**或**易失性**关键字。  
  
 *返回类型*  
 函数原型的返回类型。  
  
 *委托类型标识符*  
 声明的委托类型的名称。  
  
 *参数*  
 （可选）类型和函数原型的标识符。  
  
### <a name="remarks"></a>备注  
 使用*委托类型标识符*声明具有与委托相同的原型的事件。 有关详细信息，请参阅[委托 (C + + /cli CX)](../cppcx/delegates-c-cx.md)。  
  
### <a name="requirements"></a>要求  
 编译器选项：`/ZW`  
  
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
 （可选）在程序集外的可访问性可以是委托的公共或私有。  默认值为私有。  在类中，委托可以具有任何可访问性。  
  
 *function_declaration*  
 可以绑定到委托的函数的签名。 委托的返回类型可以是任何托管的类型。 互操作性方面的考虑，建议的委托的返回类型均为符合 CLS 类型。  
  
 若要定义未绑定的委托中的第一个参数*function_declaration*的类型应该**这**对象的指针。 
  
### <a name="remarks"></a>备注  
 委托是多播:"函数指针"可以绑定到托管类中的一个或多个方法。 **委托**关键字定义了特定方法签名的多路广播的委托类型。  
  
 委托还可以绑定到值类，如静态方法的方法。  
  
 委托具有以下特征：  
  
-   它继承自`System::MulticastDelegate`。  
  
-   它具有构造函数使用两个参数： 指向托管的类或 NULL （如果要绑定到静态方法） 和指定类型的完全限定的方法的指针。  
  
-   它具有一个称为 `Invoke` 的方法，其签名与委托的声明签名匹配。  
  
 调用委托时，其功能是已附加的顺序调用。  
  
 委托的返回值是从其最后一个附加的成员函数的返回值。  
  
 不能重载委托。  
  
 可以绑定或未绑定的委托。  
  
 当您实例化绑定的委托时，第一个参数应为对象引用。 委托实例化第二个参数应是值类型的方法是一个托管的类对象或指针的方法的地址。 委托实例化第二个参数必须使用完整的类作用域语法方法命名，并应用 address-of 运算符。  
  
 当您实例化未绑定的委托时，第一个参数应是方法的托管的类对象，则为指向值类型的方法的地址。 参数必须使用完整的类作用域语法方法命名，并应用 address-of 运算符。  
  
 在创建时指向静态或全局函数的委托，只有一个参数是必需： 函数 （（可选） 该函数的地址）。  
  
 有关委托的详细信息，请参阅  
  
-   [如何：定义和使用委托 (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)  
  
-   [泛型委托 (Visual C++)](../windows/generic-delegates-visual-cpp.md)  
  
### <a name="requirements"></a>要求  
 编译器选项：`/clr`  
  
### <a name="examples"></a>示例  
  
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
  
```Output  
in func1 8  
  
in func1 9  
  
in func2 9  
  
in func2 10  
  
in static func3 11  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)