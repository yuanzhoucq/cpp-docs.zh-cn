---
title: "编译器警告 （等级 2） C4412 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4412
dev_langs:
- C++
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
caps.latest.revision: 9
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
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 92aa12514088d0fbffbe826a495d76b49ab311d1
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-2-c4412"></a>编译器警告（等级 2）C4412
function︰ 函数签名包含类型 type;C + + 对象是不安全，以便在纯代码之间传递和混合模式或纯。  
  
 **/Clr: pure**编译器选项已弃用 Visual Studio 2015 中。  
  
 编译器检测到潜在的不安全的情况下，可能导致运行时错误︰ 调用了正在从**/clr︰ 纯**编译的函数，通过 dllimport 和函数签名已导入包含不安全类型。 一种类型是不安全的如果它包含的成员函数或有一个数据成员、 不安全类型或到不安全类型间接寻址。  
  
 这是由于在默认的调用约定纯代码和本机代码之间的差异的不安全的 （或混合本机和托管）。 在导入 (通过`dllimport`) 函数导入到**/clr: pure**编译单位，确保在签名中的每种类型的声明是导出 （要特别小心隐式调用约定之间的差异） 该函数将编译单位中的那些相同的。  
  
 虚拟成员函数是特别容易产生意外的结果。  但是，应测试甚至非虚函数，以确保获得正确的结果。 如果要确保得到正确的结果，您可以忽略此警告。  
  
 有关详细信息**/clr︰ 纯**，请参阅[如何︰ 迁移到 /clr: pure (C + + /cli CLI)](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)。  
  
 默认情况下，C4412 处于关闭状态。 请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)和[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)有关详细信息。  
  
 若要解决此警告，请从类型中移除所有函数。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4412。  
  
```  
// C4412.cpp  
// compile with: /c /W2 /clr:pure  
#pragma warning (default : 4412)  
  
struct Unsafe {  
   virtual void __cdecl Test();  
};  
  
struct Safe {  
   int i;  
};  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   Unsafe *pUnsafe = func();   // C4412  
   // pUnsafe->Test();  
  
   Safe *pSafe = func2();   // OK  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例是声明了两种类型的标头文件。 `Unsafe`类型是不安全，因为它有一个成员函数。  
  
```  
// C4412.h  
struct Unsafe {  
   // will be __clrcall if #included in pure compilation  
   // defaults to __cdecl in native or mixed mode compilation  
   virtual void Test(int * pi);  
  
   // try the following line instead  
   // virtual void __cdecl Test(int * pi);  
};  
  
struct Safe {  
   int i;  
};  
```  
  
## <a name="example"></a>示例  
 此示例使用头文件中定义的类型导出函数。  
  
```  
// C4412_2.cpp  
// compile with: /LD  
#include "C4412.h"  
  
void Unsafe::Test(int * pi) {  
   *pi++;  
}  
  
__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }  
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }  
```  
  
## <a name="example"></a>示例  
 默认调用约定**/clr: pure**编译是不同于本机编译。  包括 C4412.h 时，`Test`默认为`__clrcall`。 如果您编译并运行此程序 (请不要使用**/c**)，该程序将引发异常。  
  
 下面的示例生成 C4412。  
  
```  
// C4412_3.cpp  
// compile with: /W2 /clr:pure /c /link C4412_2.lib  
#pragma warning (default : 4412)  
#include "C4412.h"  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   int n = 7;  
   Unsafe *pUnsafe = func();   // C4412  
   pUnsafe->Test(&n);  
  
   Safe *pSafe = func2();   // OK  
}  
```
