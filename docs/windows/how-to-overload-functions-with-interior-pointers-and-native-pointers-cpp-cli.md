---
title: 如何： 用内部指针和本机指针重载函数 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c019114726f696461de58d2dc4110a3150318c8f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597996"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>如何：用内部指针和本机指针重载函数 (C++/CLI)

可以根据参数类型是内部指针或本机指针重载函数。

> [!IMPORTANT]
> `/clr` 编译器选项支持此语言功能，但是 `/ZW` 编译器选项不支持此语言功能。

## <a name="example"></a>示例

### <a name="code"></a>代码

```cpp
// interior_ptr_overload.cpp
// compile with: /clr
using namespace System;

// C++ class
struct S {
   int i;
};

// managed class
ref struct G {
   int i;
};

// can update unmanaged storage
void f( int* pi ) {
   *pi = 10;
   Console::WriteLine("in f( int* pi )");
}

// can update managed storage
void f( interior_ptr<int> pi ) {
   *pi = 10;
   Console::WriteLine("in f( interior_ptr<int> pi )");
}

int main() {
   S *pS = new S;   // C++ heap
   G ^pG = gcnew G;   // common language runtime heap
   f( &pS->i );
   f( &pG->i );
};
```

```Output 
in f( int* pi )  
in f( interior_ptr<int> pi )  
```

## <a name="see-also"></a>请参阅

[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)