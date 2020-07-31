---
title: offsetof 宏
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: ee6d5e56bb9f41a842e53984f754c7c07d58a125
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213497"
---
# <a name="offsetof-macro"></a>offsetof 宏

检索成员与其父结构的开头之间的偏移量。

## <a name="syntax"></a>语法

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>参数

*structName*<br/>
父数据结构的名称。

*名称*<br/>
确定其偏移量的父数据结构中成员的名称。

## <a name="return-value"></a>返回值

**offsetof**从其父数据结构的开头返回指定成员的偏移量（以字节为单位）。 它对于位域是未定义的。

## <a name="remarks"></a>备注

**Offsetof**宏从由*structName*指定的结构的开头作为**size_t**类型的值返回*值的偏移*量（以字节为单位）。 可以用关键字指定类型 **`struct`** 。

> [!NOTE]
> **offsetof**不是函数，无法使用 C 原型描述。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>另请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
