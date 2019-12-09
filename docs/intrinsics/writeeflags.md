---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 6b9b6976369ed810789e5749a2e30029cad4c2d7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858043"
---
# <a name="__writeeflags"></a>__writeeflags

**Microsoft 专用**

向程序状态和控制（EFLAGS）寄存器写入指定的值。

## <a name="syntax"></a>语法

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>参数

*“值”* \
中要写入到 EFLAGS 寄存器的值。 对于32位平台，`Value` 参数的长度为32位，对于64位平台为64位长。

## <a name="remarks"></a>备注

这些例程只能用作内部函数。

## <a name="requirements"></a>需求

|内部函数|体系结构|
|---------------|------------------|
|`__writeeflags`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
