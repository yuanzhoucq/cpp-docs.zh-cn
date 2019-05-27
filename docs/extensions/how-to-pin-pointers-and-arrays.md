---
title: 如何：固定指针和数组
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
ms.openlocfilehash: ae8c1da79f41cf9209f2765ce5aa2f7ca3d34aea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515682"
---
# <a name="how-to-pin-pointers-and-arrays"></a>如何：固定指针和数组

钉住在托管对象中定义的子对象能够钉住整个对象。  例如，如果数组的任何元素被钉住，则整个数组也被钉住。 没有用于声明钉住的数组的语言扩展。 若要钉住数组，请声明其元素类型的钉住指针，并钉住其中一个元素。

## <a name="example"></a>示例

### <a name="code"></a>代码

```cpp
// pin_ptr_array.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

int main() {
   array<Byte>^ arr = gcnew array<Byte>(4);
   arr[0] = 'C';
   arr[1] = '+';
   arr[2] = '+';
   arr[3] = '\0';
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned
   unsigned char * cp = p;

   printf_s("%s\n", cp); // bytes pointed at by cp
                         // will not move during call
}
```

```Output
++
```

## <a name="see-also"></a>请参阅

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)