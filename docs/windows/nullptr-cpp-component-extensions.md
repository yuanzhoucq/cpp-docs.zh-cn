---
title: nullptr （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33a276c383618531103a76b1f20c6ad478d57c10
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="nullptr--c-component-extensions"></a>nullptr（C++ 组件扩展）
`nullptr`关键字表示*null 指针值*。 使用 null 指针值指示，对象句柄、 内部指针或本机指针类型不指向对象。  
  
 使用`nullptr`与托管或本机代码。 编译器会发出适当但不同的托管和本机 null 指针值的说明。 有关使用此关键字的 ISO 标准 c + + 版本的信息，请参阅[nullptr](../cpp/nullptr.md)。  
  
 `__nullptr`关键字是具有的相同含义与 Microsoft 专用关键字`nullptr`，但适用于仅本机代码。 如果你使用`nullptr`使用本机 C/c + + 代码，并使用然后编译[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项，编译器无法确定是否`nullptr`指示本机或托管的 null 指针值。 若要使您的意图清楚地了解编译器，使用`nullptr`指定托管的值或`__nullptr`指定本机值。  
  
 `nullptr`关键字等效于`Nothing`在 Visual Basic 中和`null`C# 中。  
  
## <a name="usage"></a>用法  
 `nullptr`关键字可使用的位置可以使用句柄、 本机指针或函数参数。  
  
 `nullptr`关键字不是类型和不支持用于：  
  
-   [sizeof](../cpp/sizeof-operator.md)  
  
-   [typeid](../cpp/typeid-operator.md)  
  
-   `throw nullptr` (尽管`throw (Object^)nullptr;`起)  
  
 `nullptr`关键字可在以下的指针类型的初始化：  
  
-   本机指针  
  
-   Windows 运行时句柄  
  
-   托管的句柄  
  
-   托管的内部指针  
  
 `nullptr`关键字可以用于测试相同，如果之前使用的引用的指针或句柄引用为 null。  
  
 应正确解释语言用于错误检查 null 指针值之间的函数调用。  
  
 无法初始化为零; 的句柄仅`nullptr`可用。 常数 0 到的对象的句柄的分配生成一个装箱`Int32`和强制转换为`Object^`。  
  
## <a name="example"></a>示例  
 下面的代码示例演示`nullptr`只要的句柄，本机指针，就能使用关键字或函数参数可用。 该示例演示和`nullptr`关键字可以用于检查引用，然后使用它。  
  
```  
// mcpp_nullptr.cpp  
// compile with: /clr  
value class V {};  
ref class G {};  
void f(System::Object ^) {}  
  
int main() {  
// Native pointer.  
   int *pN = nullptr;  
// Managed handle.  
   G ^pG = nullptr;  
   V ^pV1 = nullptr;  
// Managed interior pointer.  
   interior_ptr<V> pV2 = nullptr;  
// Reference checking before using a pointer.  
   if (pN == nullptr) {}  
   if (pG == nullptr) {}  
   if (pV1 == nullptr) {}  
   if (pV2 == nullptr) {}  
// nullptr can be used as a function argument.  
   f(nullptr);   // calls f(System::Object ^)  
}  
```  
  
## <a name="example"></a>示例  
 **示例**  
  
 下面的代码示例演示`nullptr`和本机指针上互换使用零。  
  
```  
// mcpp_nullptr_1.cpp  
// compile with: /clr  
class MyClass {  
public:  
   int i;  
};  
  
int main() {  
   MyClass * pMyClass = nullptr;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
  
   pMyClass = 0;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
}  
```  
  
 **输出**  
  
```Output  
pMyClass == nullptr  
  
pMyClass == 0  
  
pMyClass == nullptr  
  
pMyClass == 0  
```  
  
## <a name="example"></a>示例  
 **示例**  
  
 下面的代码示例演示`nullptr`解释为任何类型的句柄或指向任何类型的本机指针。 如果函数重载具有不同类型的句柄时，将生成多义性错误。 `nullptr`必须显式转换为一种类型。  
  
```  
// mcpp_nullptr_2.cpp  
// compile with: /clr /LD  
void f(int *){}  
void f(int ^){}  
  
void f_null() {  
   f(nullptr);   // C2668  
   // try one of the following lines instead  
   f((int *) nullptr);  
   f((int ^) nullptr);  
}  
```  
  
## <a name="example"></a>示例  
 **示例**  
  
 下面的代码示例演示该强制转换`nullptr`允许并返回到包含的强制转换类型的指针或句柄`nullptr`值。  
  
```  
// mcpp_nullptr_3.cpp  
// compile with: /clr /LD  
using namespace System;  
template <typename T>   
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type  
  
int main() {  
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)  
  
   // Delete the following line to resolve.  
   f(nullptr);  
  
   f(0);   // T = int, call f(int)  
}  
```  
  
## <a name="example"></a>示例  
 **示例**  
  
 下面的代码示例演示`nullptr`可用作函数参数。  
  
```  
// mcpp_nullptr_4.cpp  
// compile with: /clr  
using namespace System;  
void f(Object ^ x) {  
   Console::WriteLine("test");  
}  
  
int main() {  
   f(nullptr);  
}  
```  
  
 **输出**  
  
```Output  
test  
```  
  
## <a name="example"></a>示例  
 **示例**  
  
 下面的代码示例演示当句柄声明，并且未显式初始化，它们是默认值初始化为`nullptr`。  
  
```  
// mcpp_nullptr_5.cpp  
// compile with: /clr  
using namespace System;  
ref class MyClass {  
public:  
   void Test() {  
      MyClass ^pMyClass;   // gc type  
      if (pMyClass == nullptr)  
         Console::WriteLine("NULL");  
   }  
};  
  
int main() {  
   MyClass ^ x = gcnew MyClass();  
   x -> Test();  
}  
```  
  
 **输出**  
  
```Output  
NULL  
```  
  
## <a name="example"></a>示例  
 **示例**  
  
 下面的代码示例演示`nullptr`与编译时可以分配给本机指针 **/clr**。  
  
```  
// mcpp_nullptr_6.cpp  
// compile with: /clr  
int main() {  
   int * i = 0;  
   int * j = nullptr;  
}  
```  
  
## <a name="requirements"></a>要求  
 编译器选项: (而不是所需; 支持的所有代码生成选项，包括 **/ZW**和 **/clr**)  
  
## <a name="see-also"></a>请参阅  
 [运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)   
 [nullptr](../cpp/nullptr.md)