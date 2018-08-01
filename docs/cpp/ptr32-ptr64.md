---
title: __ptr32，__ptr64 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
dev_langs:
- C++
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 050317be4c5f933ca9e08055a02555f5597c583c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406528"
---
# <a name="ptr32-ptr64"></a>__ptr32、__ptr64

**Microsoft 专用**

**__ptr32**表示本机指针在 32 位系统上，而 **__ptr64**表示 64 位系统上的本机指针。

以下示例演示如何声明所有这些指针类型：

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

 在 32 位系统上，使用声明的指针 **__ptr64**截断为 32 位指针。 在 64 位系统上，使用声明的指针 **__ptr32**强制转换为 64 位指针。

> [!NOTE]
> 不能使用 **__ptr32**或 **__ptr64**编译时 **/clr: pure**。 否则，将生成编译器错误 C2472。 **/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

## <a name="example"></a>示例

下面的示例演示如何声明和分配与指针 **__ptr32**并 **__ptr64**关键字。

```cpp
#include <cstdlib>
#include <iostream>

int main()
{
    using namespace std;

    int * __ptr32 p32;
    int * __ptr64 p64;

    p32 = (int * __ptr32)malloc(4);
    *p32 = 32;
    cout << *p32 << endl;

    p64 = (int * __ptr64)malloc(4);
    *p64 = 64;
    cout << *p64 << endl;
}
```

```Output
32
64
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅
 [基本类型](../cpp/fundamental-types-cpp.md)