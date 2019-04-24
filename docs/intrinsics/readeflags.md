---
title: __readeflags
ms.date: 11/04/2016
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: 9913fb4287e673faf79b2c352bb42eda7f590fdd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026365"
---
# <a name="readeflags"></a>__readeflags

读取程序状态和控制 (EFLAGS) 注册。

## <a name="syntax"></a>语法

```
unsigned     int __readeflags(void);
unsigned __int64 __readeflags(void);
```

## <a name="return-value"></a>返回值

EFLAGS 寄存器的值。 返回值为 32 位长时间在 32 位平台上和 64 位的 64 位平台上长时间。

## <a name="remarks"></a>备注

这些例程只能用作内部函数可使用。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readeflags`|x86、x64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__writeeflags](../intrinsics/writeeflags.md)