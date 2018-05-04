---
title: offsetof 宏 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apilocation:
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
apitype: DLLExport
f1_keywords:
- offsetof
dev_langs:
- C++
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 308aac2493751cfe2147187ed9848347124a90d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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

*成员名称*<br/>
确定其偏移量的父数据结构中成员的名称。

## <a name="return-value"></a>返回值

**offsetof**从其父数据结构的开头，以字节为单位指定成员返回的偏移量。 它对于位域是未定义的。

## <a name="remarks"></a>备注

**Offsetof**宏返回以字节为单位的偏移量*memberName*从指定的结构的开头*structName*类型的值作为**size_t**。 你可以指定与类型**结构**关键字。

> [!NOTE]
> **offsetof**不是函数和不能使用 C 原型描述。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[内存分配](../../c-runtime-library/memory-allocation.md)<br/>
