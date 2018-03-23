---
title: pin_ptr (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
dev_langs:
- C++
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce63996cc2d93f4890f54c5edda318fca55f98aa
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)
声明*钉住指针*，其只能与公共语言运行时一起使用。  
  
## <a name="all-runtimes"></a>所有运行时  
 （此语言功能没有适用于所有运行时的备注。）  
  
## <a name="windows-runtime"></a>Windows 运行时  
 （此语言功能不支持在 Windows 运行时中。）  
  
## <a name="common-language-runtime"></a>公共语言运行时  
 A*钉住指针*可防止该对象的内部指针指向在垃圾回收堆上移动。 也就是说，公共语言运行时不会更改钉住指针的值。 这是必需的当您将托管类的地址传递到非托管函数中的地址不会意外更改在解析非托管的函数调用的过程。  
  
### <a name="syntax"></a>语法  
  
```cpp  
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;  
```  
  
### <a name="parameters"></a>参数  
 *cv_qualifier*  
 `const` 或`volatile`限定符。 默认情况下，钉住指针是`volatile`。 但不是声明钉住指针是错误多余`volatile`。  
  
 *type*  
 `initializer` 的类型。  
  
 *var*  
 `pin_ptr` 变量的名称。  
  
 *initializer*  
 可以分配给本机指针的引用类型、托管数组的元素或者任何其他对象的成员。  
  
### <a name="remarks"></a>备注  
 A`pin_ptr`表示本机指针的功能的超集。 因此，可以分配给本机指针的任何内容还可以分配到`pin_ptr`。 内部指针允许执行与本机指针相同的操作，其中包括比较和指针算法。  
  
 对象或子对象的托管类可以固定，在这种情况下公共语言运行时不会移动它在垃圾回收期间。 主要用途是将指针传递给托管数据作为实际参数的非托管的函数调用。 在出现集合周期中，运行时将检查为钉住指针创建的元数据，并将不会移动它指向的项。  
  
 固定对象还钉住其值字段中;也就是说，基元的字段或值类型。 但是，通过跟踪句柄声明的字段 (`%`) 不固定。  
  
 钉住在托管对象中定义的子对象具有固定整个对象的效果。  
  
 如果重新分配钉住指针以指向新值，指向上一个实例就不再被视为固定。  
  
 固定对象仅而`pin_ptr`指向了它。 对象不再固定时其固定指针超出范围，或设置为[nullptr](../windows/nullptr-cpp-component-extensions.md)。 后`pin_ptr`超出范围，已固定的对象可以通过垃圾回收器堆中移动。 将不会更新任何仍指向对象的本机指针，并取消引用至少其中一个可能会产生不可恢复的异常。  
  
 如果没有钉住指针指向的对象 (所有的固定指针超出作用域、 以及重新分配为指向其他对象，或已分配[nullptr](../windows/nullptr-cpp-component-extensions.md))，该对象保证不固定。  
  
 钉住指针可以指向引用句柄、 值类型或装箱的类型句柄、 托管类型的成员或托管数组的元素。 它不能指向引用类型。  
  
 采用的地址`pin_ptr`指向本机对象会导致未定义的行为。  
  
 钉住指针只能声明为非静态局部变量堆栈上。  
  
 不能用作钉住指针：  
  
-   函数参数  
  
-   函数的返回类型  
  
-   类的成员  
  
-   强制转换的目标类型。  
  
 `pin_ptr` 处于`cli`命名空间。 有关详细信息，请参阅[平台、 default 和 cli 命名空间](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
 有关内部指针的详细信息，请参阅[interior_ptr (C + + /cli CLI)](../windows/interior-ptr-cpp-cli.md)。  
  
 有关钉住指针的详细信息，请参阅[How to: Pin 指针和数组](../windows/how-to-pin-pointers-and-arrays.md)和[如何： 声明钉住指针和值类型](../windows/how-to-declare-pinning-pointers-and-value-types.md)。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的示例使用`pin_ptr`来约束的数组的第一个元素的位置。  
  
```  
// pin_ptr_1.cpp  
// compile with: /clr   
using namespace System;  
#define SIZE 10  
  
#pragma unmanaged  
// native function that initializes an array  
void native_function(int* p) {  
   for(int i = 0 ; i < 10 ; i++)  
    p[i] = i;  
}  
#pragma managed  
  
public ref class A {  
private:  
   array<int>^ arr;   // CLR integer array  
  
public:  
   A() {  
      arr = gcnew array<int>(SIZE);  
   }  
  
   void load() {  
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr  
   int* np = p;   // pointer to the first element in arr  
   native_function(np);   // pass pointer to native function  
   }  
  
   int sum() {  
      int total = 0;  
      for (int i = 0 ; i < SIZE ; i++)  
         total += arr[i];  
      return total;  
   }  
};  
  
int main() {  
   A^ a = gcnew A;  
   a->load();   // initialize managed array using the native function  
   Console::WriteLine(a->sum());  
}  
```  
  
 **输出**  
  
```Output  
45  
```  
  
 **示例**  
  
 下面的示例演示内部指针可转换为钉住指针和返回类型的 address-of 运算符 (`&`) 是一个内部指针，如果操作数是托管堆上。  
  
```  
// pin_ptr_2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   G() : i(1) {}  
   int i;  
};  
  
ref struct H {  
   H() : j(2) {}  
   int j;  
};  
  
int main() {  
   G ^ g = gcnew G;   // g is a whole reference object pointer  
   H ^ h = gcnew H;  
  
   interior_ptr<int> l = &(g->i);   // l is interior pointer  
  
   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer  
  
   k = l;   // ok  
   Console::WriteLine(*k);  
};  
```  
  
 **输出**  
  
```Output  
1  
```  
  
 **示例**  
  
 下面的示例演示钉住指针可转换为另一种类型。  
  
```  
// pin_ptr_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class ManagedType {  
public:  
   int i;  
};  
  
int main() {  
   ManagedType ^mt = gcnew ManagedType;  
   pin_ptr<int> pt = &mt->i;  
   *pt = 8;  
   Console::WriteLine(mt->i);  
  
   char *pc = ( char* ) pt;  
   *pc = 255;  
   Console::WriteLine(mt->i);  
}  
```  
  
 **输出**  
  
```Output  
8  
255  
```