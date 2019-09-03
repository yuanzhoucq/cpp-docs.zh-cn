---
title: __incfsbyte, __incfsword, __incfsdword
ms.date: 09/02/2019
f1_keywords:
- __incfsword
- __incfsbyte_cpp
- __incfsbyte
- __incfsdword
- __incfsword_cpp
- __incfsdword_cpp
helpviewer_keywords:
- __incfsword intrinsic
- __incfsdword intrinsic
- __incfsbyte intrinsic
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
ms.openlocfilehash: 43824829043304f5762d049b5c75a72b57e2102c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222125"
---
# <a name="__incfsbyte-__incfsword-__incfsdword"></a>__incfsbyte, __incfsword, __incfsdword

**Microsoft 专用**

在相对于`FS`段开头的偏移量指定的内存位置, 向值添加一个值。

## <a name="syntax"></a>语法

```C
void __incfsbyte(
   unsigned long Offset
);
void __incfsword(
   unsigned long Offset
);
void __incfsdword(
   unsigned long Offset
);
```

### <a name="parameters"></a>参数

*抵销*\
中与开头`FS`之间的偏移量。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__incfsbyte`|x86|
|`__incfsword`|x86|
|`__incfsdword`|x86|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

这些内部函数仅在内核模式下可用, 且例程只能用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[\__addfsbyte、 \__addfsword、 \__addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)\
[\__readfsbyte、 \__readfsdword、 \__readfsqword、 \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[\__writefsbyte、 \__writefsdword、 \__writefsqword、 \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
