---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: e43789d2fbed1bdc52665531c61c6c932a27f5ab
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219147"
---
# <a name="__writeeflags"></a>__writeeflags

向程序状态和控制 (EFLAGS) 寄存器写入指定的值。

## <a name="syntax"></a>语法

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>参数

*负值*\
中要写入到 EFLAGS 寄存器的值。 对于`Value` 32 位平台, 此参数的长度为32位, 对于64平台为64位长。

## <a name="remarks"></a>备注

这些例程只能用作内部函数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__writeeflags`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
