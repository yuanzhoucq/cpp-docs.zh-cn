---
title: 如何：封送嵌入式指针使用C++互操作
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], marshaling embedded pointers
- interop [C++], embedded pointers
- C++ Interop, embedded pointers
- marshaling [C++], embedded pointers
- pointers [C++], marshaling
- data marshaling [C++], embedded pointers
ms.assetid: 05fb8858-97f2-47aa-86b2-2c0ad713bdb2
ms.openlocfilehash: c6d622060aaf700b6ea1a3bfe797ab3190eee797
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345743"
---
# <a name="how-to-marshal-embedded-pointers-using-c-interop"></a>如何：封送嵌入式指针使用C++互操作

下面的代码示例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指令以实现托管和非托管函数中同一文件中，但如果在单独的文件中定义，这些函数互操作方式相同。 文件仅包含非托管的函数无需使用编译[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>示例

下面的示例演示可以如何从托管函数调用非托管的函数采用包含指针的结构。 托管的函数创建该结构的实例并初始化使用 new 关键字对嵌入的指针 (而不是[ref new、 gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)关键字)。 此分配本机堆上的内存，因为没有需要固定要禁止显示垃圾回收的数组。 但是，必须显式删除内存以避免内存泄漏。

```
// marshal_embedded_pointer.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

// unmanaged struct
struct ListStruct {
   int count;
   double* item;
};

#pragma unmanaged

void UnmanagedTakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}

#pragma managed

int main() {
   ListStruct list;
   list.count = 10;
   list.item = new double[list.count];

   Console::WriteLine("[managed] count = {0}", list.count);
   Random^ r = gcnew Random(0);
   for (int i=0; i<list.count; i++) {
      list.item[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, list.item[i]);
   }

   UnmanagedTakesListStruct( list );
   delete list.item;
}
```

```Output
[managed] count = 10
array[0] = 72.624326996796
array[1] = 81.7325359590969
array[2] = 76.8022689394663
array[3] = 55.8161191436537
array[4] = 20.6033154021033
array[5] = 55.8884794618415
array[6] = 90.6027066011926
array[7] = 44.2177873310716
array[8] = 97.754975314138
array[9] = 27.370445768987
[unmanaged] count = 10
array[0] = 72.624327
array[1] = 81.732536
array[2] = 76.802269
array[3] = 55.816119
array[4] = 20.603315
array[5] = 55.888479
array[6] = 90.602707
array[7] = 44.217787
array[8] = 97.754975
array[9] = 27.370446
```

## <a name="see-also"></a>请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
