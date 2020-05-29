---
title: _CIlog
ms.date: 4/2/2020
api_name:
- _CIlog
- _o__CIlog
api_location:
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CIlog
- CIlog
helpviewer_keywords:
- _CIlog intrinsic
- CIlog intrinsic
ms.assetid: 23503854-ddaa-4fe0-a4a3-7fbb3a43bdec
ms.openlocfilehash: 405af59eab918498578c2d62c66be1017ecf156f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918062"
---
# <a name="_cilog"></a>_CIlog

计算堆栈顶部值的自然对数。

## <a name="syntax"></a>语法

```cpp
void __cdecl _CIlog();
```

## <a name="remarks"></a>备注

此版本的 `log` 函数具有编译器理解的专用化调用约定。 它将加快执行的速度，因为它可防止生成副本和帮助注册表分配。

生成的值被将被推送到堆栈顶部。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](global-state.md)。

## <a name="requirements"></a>要求

**平台：** x86

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[log、logf、log10、log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)
