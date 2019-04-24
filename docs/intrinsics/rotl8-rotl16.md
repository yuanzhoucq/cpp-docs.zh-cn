---
title: _rotl8、_rotl16
ms.date: 11/04/2016
f1_keywords:
- _rotl8
- _rotl16
helpviewer_keywords:
- _rotl8 intrinsic
- _rotl16 intrinsic
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
ms.openlocfilehash: 8c87c7a5fa1c2bee475b0e4508b5c1571dc449de
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028284"
---
# <a name="rotl8-rotl16"></a>_rotl8、_rotl16

**Microsoft 专用**

通过指定的位位置数将输入值旋转到最高有效位 (MSB) 左侧。

## <a name="syntax"></a>语法

```
unsigned char _rotl8(
   unsigned char value,
   unsigned char shift
);
unsigned short _rotl16(
   unsigned short value,
   unsigned char shift
);
```

#### <a name="parameters"></a>参数

*值*<br/>
[in]要旋转的值。

*shift*<br/>
[in]要旋转的位数目。

## <a name="return-value"></a>返回值

旋转的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_rotl8`|x86、 ARM、 x64|
|`_rotl16`|x86、 ARM、 x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

不像左移操作，当执行向左旋转时，离开高端的高序位将移动到最低有效位位置。

## <a name="example"></a>示例

```
// rotl.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_rotl8, _rotl16)

int main()
{
    unsigned char c = 'A', c1, c2;

    for (int i = 0; i < 8; i++)
    {
       printf_s("Rotating 0x%x left by %d bits gives 0x%x\n", c,
               i, _rotl8(c, i));
    }

    unsigned short s = 0x12;
    int nBit = 10;

    printf_s("Rotating unsigned short 0x%x left by %d bits gives 0x%x\n",
            s, nBit, _rotl16(s, nBit));
}
```

```Output
Rotating 0x41 left by 0 bits gives 0x41
Rotating 0x41 left by 1 bits gives 0x82
Rotating 0x41 left by 2 bits gives 0x5
Rotating 0x41 left by 3 bits gives 0xa
Rotating 0x41 left by 4 bits gives 0x14
Rotating 0x41 left by 5 bits gives 0x28
Rotating 0x41 left by 6 bits gives 0x50
Rotating 0x41 left by 7 bits gives 0xa0
Rotating unsigned short 0x12 left by 10 bits gives 0x4800
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_rotr8, _rotr16](../intrinsics/rotr8-rotr16.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)