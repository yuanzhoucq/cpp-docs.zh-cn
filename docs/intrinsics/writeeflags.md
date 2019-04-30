---
title: __writeeflags
ms.date: 11/04/2016
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 6679a3b16def3ed413c5cec2a4bb7d5fe5d732c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389913"
---
# <a name="writeeflags"></a>__writeeflags

指定的值写入程序状态和控件 (EFLAGS) 注册。

## <a name="syntax"></a>语法

```
void __writeeflags(unsigned Value);
void __writeeflags(unsigned __int64 Value);
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*值*|[in]要写入到 EFLAGS 寄存器的值。 `Value`参数为 32 位长的 32 位平台和 64 位长的时间在 64 位平台。|

## <a name="remarks"></a>备注

这些例程只能用作内部函数可使用。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__writeeflags`|x86、x64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__readeflags](../intrinsics/readeflags.md)