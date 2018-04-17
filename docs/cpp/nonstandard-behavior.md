---
title: "非标准行为 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 967f182451c712b46c5f2da545d2fed7ffd59bca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nonstandard-behavior"></a>非标准行为
以下几节将列出 C++ 的 Visual C++ 实现不遵循 C++ 标准的几处地方。 下面给出的节号引用了 C++ 11 标准 (ISO/IEC 14882:2011(E)) 中的节号。  
  
 编译器限制不同的 C++ 标准中所定义的列表中提供了[编译器限制](../cpp/compiler-limits.md)。  
  
## <a name="covariant-return-types"></a>协变返回类型  
 当虚函数具有可变数量的参数时，不支持虚拟基类作为协变返回类型。 这不符合 C++ ISO 规范第 10.3 节第 7 段。 下面的示例无法进行编译，产生编译器错误[C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)  
  
```cpp  
// CovariantReturn.cpp  
class A   
{  
   virtual A* f(int c, ...);   // remove ...  
};  
  
class B : virtual A  
{  
   B* f(int c, ...);   // C2688 remove ...  
};  
```  
  
## <a name="binding-nondependent-names-in-templates"></a>绑定模板中的非依赖性名称  
 在最初分析模板时，Visual C++ 编译器当前不支持绑定非依赖性名称。 这不符合 C++ ISO 规范的第 14.6.3 节。 这可能导致在模板之后（但在模板实例化之前）声明的重载出现。  
  
```cpp  
#include <iostream>  
using namespace std;  
  
namespace N {  
   void f(int) { cout << "f(int)" << endl;}  
}  
  
template <class T> void g(T) {  
    N::f('a');   // calls f(char), should call f(int)  
}  
  
namespace N {  
    void f(char) { cout << "f(char)" << endl;}  
}  
  
int main() {  
    g('c');  
}  
// Output: f(char)  
  
```  
  
## <a name="function-exception-specifiers"></a>函数异常说明符  
 分析但不使用除 `throw()` 以外的函数异常说明符。 这不符合 ISO C++ 规范的第 15.4 节。 例如:  
  
```cpp  
void f() throw(int); // parsed but not used  
void g() throw();    // parsed and used  
```  
  
 有关异常规范的详细信息，请参阅[异常规范](../cpp/exception-specifications-throw-cpp.md)。  
  
## <a name="chartraitseof"></a>char_traits::eof()  
 C++ 标准声明[char_traits:: eof](../standard-library/char-traits-struct.md#eof)不能对应于一个有效`char_type`值。 Visual C++ 编译器对 `char` 类型强制实行该约束，但不对 `wchar_t` 类型实行。 这不符合 C++ ISO 规范的第 12.1.1 节中表 62 的需求。 下面的示例将说明这一点。  
  
```cpp  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    char_traits<char>::int_type int2 = char_traits<char>::eof();  
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;  
  
    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();  
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;  
}  
```  
  
## <a name="storage-location-of-objects"></a>对象的存储位置  
 C++ 标准（第 1.8 节第 6 段）要求完整的 C++ 对象具有唯一的存储位置。 但是，在使用 Visual C++ 时存在这样的情况：无数据成员的类型将与对象的生存期的其他类型共享存储位置。