---
title: _AddressOfReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: 79d1e4645c60fb4231a53aaefdcf1fe0f3c876c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62264798"
---
# <a name="addressofreturnaddress"></a>_AddressOfReturnAddress

**Microsoft 专用**

提供了保留当前函数的返回地址的内存位置的地址。 不可能使用此地址来访问其他内存位置 （例如，函数的自变量）。

## <a name="syntax"></a>语法

```
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

当`_AddressOfReturnAddress`编译的程序中使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)，函数包含`_AddressOfReturnAddress`调用编译为本机函数。 当函数编译为托管函数包含调用`_AddressOfReturnAddress`，`_AddressOfReturnAddress`可能会发生意外行为。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```
// compiler_intrinsics_AddressOfReturnAddress.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

// This function will print three values:
//   (1) The address retrieved from _AddressOfReturnAdress
//   (2) The return address stored at the location returned in (1)
//   (3) The return address retrieved the _ReturnAddress* intrinsic
// Note that (2) and (3) should be the same address.
__declspec(noinline)
void func() {
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();
   printf_s("%p\n", pvAddressOfReturnAddress);
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));
   printf_s("%p\n", _ReturnAddress());
}

int main() {
   func();
}
```

```Output
0012FF78
00401058
00401058
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[关键字](../cpp/keywords-cpp.md)