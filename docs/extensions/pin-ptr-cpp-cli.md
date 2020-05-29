---
title: pin_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
ms.openlocfilehash: 920135943c9dfb46b00ee6ceb2535fde128dffb0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172030"
---
# <a name="pin_ptr-ccli"></a>pin_ptr (C++/CLI)

声明固定指针，此指针仅适用于公共语言运行时。

## <a name="all-runtimes"></a>所有运行时

（此语言功能没有适用于所有运行时的备注。）

## <a name="windows-runtime"></a>Windows 运行时

（Windows 运行时不支持此语言功能。）

## <a name="common-language-runtime"></a>公共语言运行时

固定指针是一个内部指针，可防止指向的对象在垃圾回收堆上移动。 也就是说，公共语言运行时不会更改固定指针的值。 向未托管的函数传递托管类的地址时，必须使用此指针，这样地址就不会在解析未托管的函数调用过程中意外更改。

### <a name="syntax"></a>语法

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>parameters

cv_qualifier<br/>
const 或 volatile 限定符。 默认情况下，固定指针为 volatile。 将固定指针声明为 volatile 虽是多余做法，但并不是错误做法。

type<br/>
初始值设定项的类型。

*var*<br/>
pin_ptr 变量的名称。

*initializer*<br/>
可以分配给本机指针的引用类型、托管数组的元素或者任何其他对象的成员。

### <a name="remarks"></a>备注

pin_ptr 表示本机指针的功能超集。 因此，可以分配给本机指针的所有内容也可以分配给 pin_ptr。 内部指针允许执行与本机指针相同的操作，其中包括比较和指针算法。

可以固定托管类的对象或子对象，在这种情况下，公共语言运行时不会在垃圾回收期间移动它。 它的主要用途是，将指向托管数据的指针作为未托管的函数调用的实际参数进行传递。 在回收周期内，运行时会检查为固定指针创建的元数据，但不会移动它指向的项。

固定一个对象还会固定它的值字段，即基元类型或值类型的字段。 不过，不会固定通过跟踪句柄 (`%`) 声明的字段。

固定在托管对象中定义的子对象具有固定整个对象的效果。

如果将固定指针重新分配为指向新值，指向的旧实例就不再视为固定。

对象只有在 pin_ptr 指向它时才会固定。 如果对象的固定指针超出范围或设置为 [nullptr](nullptr-cpp-component-extensions.md)，对象就不再固定。 在 pin_ptr 超出范围后，垃圾回收器可以在堆中移动之前固定的对象。 任何仍指向此对象的本机指针都不会进行更新，如果取消引用其中一个指针，可能会抛出不可恢复的异常。

如果没有固定指针指向对象（所有固定指针都超出了范围、重新分配为指向其他对象，或分配有 [nullptr](nullptr-cpp-component-extensions.md)），那么对象保证不会固定。

固定指针可以指向引用句柄、值类型或装箱类型句柄、托管类型的成员或托管数组的元素。 但无法指向引用类型。

获取指向本机对象的 pin_ptr 的地址会导致未定义的行为发生。

固定指针只能声明为堆栈上的非静态本地变量。

固定指针无法用作：

- 函数参数

- 函数的返回类型

- 类成员

- 强制转换的目标类型。

pin_ptr 位于 `cli` 命名空间中。 有关详细信息，请参阅[平台默认 cli 命名空间](platform-default-and-cli-namespaces-cpp-component-extensions.md)。

若要详细了解内部指针，请参阅 [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)。

有关固定指针的详细信息，请参阅[如何：固定指针和数组](how-to-pin-pointers-and-arrays.md)和[如何：声明钉住指针和值类型](how-to-declare-pinning-pointers-and-value-types.md)。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的示例使用 pin_ptr 来约束数组中第一个元素的位置。

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

下面的示例展示了，可以将内部指针转换为固定指针，并且当操作数位于托管堆上时，取址器运算符 (`&`) 的返回类型是内部指针。

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

下面的示例展示了可以将固定指针强制转换为其他类型。

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
