---
title: pin_ptr (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af0cfe6f3a94aa1bc2afc4e4857864f81099567e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591726"
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)

声明*钉住指针*，仅使用公共语言运行时使用。

## <a name="all-runtimes"></a>所有运行时

（此语言功能没有适用于所有运行时的备注。）

## <a name="windows-runtime"></a>Windows 运行时

（此语言功能不支持在 Windows 运行时中。）

## <a name="common-language-runtime"></a>公共语言运行时

一个*钉住指针*可防止该对象的内部指针指向在垃圾回收堆上移动。 也就是说，钉住指针的值不会更改公共语言运行时。 当你将托管类的地址传递给非托管函数中地址不会意外更改在解析非托管的函数调用过程时，这是必需的。

### <a name="syntax"></a>语法

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>参数

*cv_qualifier*  
**const**或**易失性**限定符。 默认情况下是钉住指针**易失性**。 做法是多余的但不是错误声明钉住指针**易失性**。

*type*  
类型*初始值设定项*。

*var*  
名称**pin_ptr**变量。

*initializer*  
可以分配给本机指针的引用类型、托管数组的元素或者任何其他对象的成员。

### <a name="remarks"></a>备注

一个**pin_ptr**表示本机指针的功能超集。 因此，可以分配给本机指针的任何内容还可以分配给**pin_ptr**。 内部指针允许执行与本机指针相同的操作，其中包括比较和指针算法。

对象或子对象的托管类可以将固定，在这种情况下公共语言运行时不会移动它在垃圾回收期间。 主要用途是将指针传递给托管的数据，作为非托管的函数调用的实际参数。 在一个集合周期内，运行时将检查为钉住指针创建的元数据并不会移动它指向的项。

将对象固定还固定其值字段中;也就是说，基元字段或值类型。 但是，字段声明的跟踪句柄 (`%`) 不固定。

固定托管对象中定义的子对象具有固定整个对象的效果。

钉住指针重新分配来指向新值，如果在前一个实例指向不再被视为固定。

固定对象而**pin_ptr**指向了它。 对象不再固定时其固定指针超出范围，或设置为[nullptr](../windows/nullptr-cpp-component-extensions.md)。 之后**pin_ptr**超出范围，固定的对象可以通过垃圾回收器堆中移动。 将不会更新任何仍指向对象的本机指针，并取消引用其中一个可能会产生不可恢复的异常。

如果没有钉住指针指向的对象 (所有钉住指针超出作用域，以及重新分配以指向其他对象，或已分配[nullptr](../windows/nullptr-cpp-component-extensions.md))，该对象保证不固定。

钉住指针可以指向引用句柄、 值类型或装箱的类型句柄、 托管类型的成员或托管数组的元素。 它不能指向引用类型。

采用的地址**pin_ptr**指向本机对象会导致未定义的行为。

钉住指针仅可以作为非静态本地变量在堆栈上声明。

不能用作钉住指针：

- 函数参数

- 函数的返回类型

- 类的成员

- 强制转换的目标类型。

**pin_ptr**处于`cli`命名空间。 有关详细信息，请参阅[Platform、 default 和 cli 命名空间](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。

有关内部指针的详细信息，请参阅[interior_ptr (C + + CLI)](../windows/interior-ptr-cpp-cli.md)。

钉住指针的详细信息，请参阅[如何： Pin 指针和数组](../windows/how-to-pin-pointers-and-arrays.md)并[如何： 声明钉住指针和值类型](../windows/how-to-declare-pinning-pointers-and-value-types.md)。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的示例使用**pin_ptr**来约束数组的第一个元素的位置。

```cpp
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

```Output
45
```

下面的示例演示内部指针可转换为钉住指针和返回类型的 address-of 运算符 (`&`) 是一个操作数是托管堆上的内部指针。

```cpp
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

```Output
1
```

下面的示例演示固定指针可以转换为其他类型。

```cpp
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

```Output
8
255
```