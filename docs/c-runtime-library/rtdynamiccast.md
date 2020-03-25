---
title: __RTDynamicCast
ms.date: 11/04/2016
api_name:
- __RTDynamicCast
api_location:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __RTDynamicCast
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
ms.openlocfilehash: a5384966ff96c4e4831ba06f7c67467156a9ecd2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170067"
---
# <a name="__rtdynamiccast"></a>__RTDynamicCast

[dynamic_cast](../cpp/dynamic-cast-operator.md) 运算符的运行时实现。

## <a name="syntax"></a>语法

```cpp
PVOID __RTDynamicCast (
   PVOID inptr,
   LONG VfDelta,
   PVOID SrcType,
   PVOID TargetType,
   BOOL isReference
   ) throw(...)
```

#### <a name="parameters"></a>parameters

*inptr*<br/>
指向多态对象的指针。

*VfDelta*<br/>
对象中的虚函数指针的偏移量。

*SrcType*<br/>
由 `inptr` 参数指向的对象的静态类型。

*TargetType*<br/>
转换的预期结果。

*isReference*<br/>
如果输入是引用，则为“true”；如果输入是指针，则为“false”。

## <a name="return-value"></a>返回值

如果成功，则为指向适当的子对象的指针；否则为 NULL。

## <a name="exceptions"></a>例外

如果 `bad_cast()` 的输入为引用并且转换失败，则为 `dynamic_cast<>`。

## <a name="remarks"></a>备注

将 `inptr` 转换为 `TargetType` 类型的对象。 如果 `inptr` 是指针，则 `TargetType` 类型必须为指针，或者如果 `TargetType` 是引用，则为左值。 `TargetType` 必须是针对以前定义的类类型的指针或引用，或者是指向 void 的指针。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|
