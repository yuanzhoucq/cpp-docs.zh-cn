---
title: _CIatan
ms.date: 4/2/2020
api_name:
- _CIatan
- _o__CIatan
api_location:
- msvcr120.dll
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CIatan
- CIatan
helpviewer_keywords:
- CIatan intrinsic
- _CIatan intrinsic
ms.assetid: 3baa0429-fe46-4bab-8b00-868e2186dc8c
ms.openlocfilehash: 7b3f70ebcf6debbf5fe881fc0c64b407b9bd4ef3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334406"
---
# <a name="_ciatan"></a>_CIatan

计算堆栈顶部值的反正切值。

## <a name="syntax"></a>语法

```
void __cdecl _CIatan();
```

## <a name="remarks"></a>备注

此版本的 `atan` 函数具有编译器理解的专用化调用约定。 它将加快执行的速度，因为它可防止生成副本和帮助注册表分配。

生成的值被将被推送到堆栈顶部。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](global-state.md)。

## <a name="requirements"></a>要求

**平台：** x86

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)
