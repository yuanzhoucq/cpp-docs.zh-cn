---
title: _mm_cvtsi64x_ss
ms.date: 11/04/2016
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 4b8d0e1a19441cd671143843ae4ac6e89bfeae50
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328937"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss

**Microsoft 专用**

生成扩展的 x64 版本的标量单精度浮点值将转换的 64 位整数 (`cvtsi2ss`) 指令。

## <a name="syntax"></a>语法

```
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

#### <a name="parameters"></a>参数

*a*<br/>
[in]`__m128`结构，它包含四个单精度浮点值。

*b*<br/>
[in]要转换为浮点值 64 位整数。

## <a name="return-value"></a>返回值

`__m128`结构，其第一个浮点值是转换的结果。 其他三个值复制相比并无变化`a`。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|X64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

`__m128`结构表示 XMM 寄存器，因此此内部函数，允许的值`b`从系统内存，无法移动到 XMM 注册。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__m128](../cpp/m128.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)