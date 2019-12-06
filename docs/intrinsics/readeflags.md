---
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: 6afdc0f20a3ae72865a80ba2eb7f896f79f63171
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857900"
---
# <a name="__readeflags"></a>__readeflags

**Microsoft 专用**

读取程序状态和控制（EFLAGS）注册。

## <a name="syntax"></a>语法

```C
unsigned     int __readeflags(void); /* x86 */
unsigned __int64 __readeflags(void); /* x64 */
```

## <a name="return-value"></a>返回值

EFLAGS 寄存器的值。 32位平台上的返回值为32位长，而在64位平台上为64位长。

## <a name="remarks"></a>备注

这些例程只能用作内部函数。

## <a name="requirements"></a>需求

|内部函数|体系结构|
|---------------|------------------|
|`__readeflags`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__writeeflags](../intrinsics/writeeflags.md)
