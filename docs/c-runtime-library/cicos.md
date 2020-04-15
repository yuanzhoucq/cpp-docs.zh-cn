---
title: _CIcos
ms.date: 4/2/2020
api_name:
- _CIcos
- _o__CIcos
api_location:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIcos
- _CIcos
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
ms.openlocfilehash: e7009272dbbd2b406c6355977514feaaf13ba746
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334378"
---
# <a name="_cicos"></a>_CIcos

计算浮点堆栈顶部值的余弦值。

## <a name="syntax"></a>语法

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>备注

此版本的 [cos](../c-runtime-library/reference/cos-cosf-cosl.md) 函数具有编译器理解的专用化调用约定。 它将加快执行的速度，因为它可防止生成副本和帮助注册表分配。

生成的值被将被推送到浮点堆栈顶部。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](global-state.md)。

## <a name="requirements"></a>要求

**平台：** x86

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[cos、cosf、cosl](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
