---
title: __emul, __emulu
ms.date: 11/04/2016
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
ms.openlocfilehash: 8657c0fb034ac6bbcfbebb946e059ad08d9e7046
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030045"
---
# <a name="emul-emulu"></a>__emul, __emulu

**Microsoft 专用**

执行乘法运算溢出的 32 位整数可以容纳。

## <a name="syntax"></a>语法

```
__int64 __emul(
   int a,
   int b
);
unsigned __int64 __emulu(
   unsigned int a,
   unsigned int b
);
```

#### <a name="parameters"></a>参数

*a*<br/>
[in]该乘法运算的第一个整数操作数。

*b*<br/>
[in]该乘法运算的第二个整数操作数。

## <a name="return-value"></a>返回值

该乘法运算的结果。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__emul`|x86、x64|
|`__emulu`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

`__emul` 采用两个 32 位有符号的值并返回作为 64 位有符号的整数值相乘的结果。

`__emulu` 采用两个 32 位无符号的整数值，并返回作为 64 位无符号的整数值相乘的结果。

## <a name="example"></a>示例

```
// emul.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__emul)
#pragma intrinsic(__emulu)

int main()
{
   int a = -268435456;
   int b = 2;

   __int64 result = __emul(a, b);

   cout << a << " * " << b << " = " << result << endl;

   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295
   unsigned int ub = 0xF000000;  // Dec value: 251658240

   unsigned __int64 uresult = __emulu(ua, ub);

   cout << ua << " * " << ub << " = " << uresult << endl;

}
```

## <a name="output"></a>Output

```
-268435456 * 2 = -536870912
4294967295 * 251658240 = 1080863910317260800
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)