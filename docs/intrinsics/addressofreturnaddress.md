---
title: _AddressOfReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: d705029c30fdbc117c4c6e96923691e43e072e23
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221073"
---
# <a name="_addressofreturnaddress"></a>_AddressOfReturnAddress

**Microsoft 专用**

提供保存当前函数的返回地址的内存位置的地址。 此地址不能用于访问其他内存位置 (例如, 函数的参数)。

## <a name="syntax"></a>语法

```C
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86、x64、ARM、ARM64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

当`_AddressOfReturnAddress`在使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译的程序中使用时, 包含该`_AddressOfReturnAddress`调用的函数将编译为本机函数。 当编译为对包含`_AddressOfReturnAddress`的函数的托管调用的函数时, `_AddressOfReturnAddress`可能不会按预期方式运行。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```cpp
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

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[关键字](../cpp/keywords-cpp.md)
