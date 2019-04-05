---
title: __shiftright128
ms.date: 11/04/2016
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: b721abc9be22709fdc221951e2012300d6b96762
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030097"
---
# <a name="shiftright128"></a>__shiftright128

**Microsoft 专用**

将 128 位数量（表示为两个 64 位数量 `LowPart` 和 `HighPart`）按 `Shift` 指定的位数右移并返回低 64 位结果。

## <a name="syntax"></a>语法

```
unsigned __int64 __shiftright128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

#### <a name="parameters"></a>参数

*LowPart*<br/>
[in]要位移的 128 位数量的低 64 位。

*HighPart*<br/>
[in]要位移的 128 位数量高 64 位。

*移位*<br/>
[in]移动的位数数。

## <a name="return-value"></a>返回值

结果的低 64 位。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__shiftright128`|X64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

`Shift` 值始终是模 64，如果调用 `__shiftright128(0, 1, 64)`，该函数将向右位移高部分 `0` 位并返回低部分的 `0` 而不是另外预期的 `1`。

## <a name="example"></a>示例

有关示例，请参阅[__shiftleft128](../intrinsics/shiftleft128.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__shiftleft128](../intrinsics/shiftleft128.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)