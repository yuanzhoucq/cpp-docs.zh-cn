---
title: _purecall
ms.date: 4/2/2020
api_name:
- _purecall
- _o__purecall
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: f841bc70a4a5365bb9cc6086dd752bd2a1b583ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338490"
---
# <a name="_purecall"></a>_purecall

默认纯虚拟函数调用错误处理程序。 当调用纯虚拟成员函数时，编译器生成调用此函数的代码。

## <a name="syntax"></a>语法

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>备注

**_purecall**函数是 Microsoft C++编译器的特定于 Microsoft 的实现详细信息。 此函数不可以直接通过代码调用，也没有任何公用标头声明。 之所以在这里讨论此函数，是因为它是 C 运行时库的公用导出。

对纯虚拟函数的调用出错，因为它没有实现。 调用纯虚拟函数时，编译器将生成代码以调用 **_purecall**错误处理程序函数。 默认情况下 **，_purecall**终止程序。 在终止之前，如果已为进程设置了 **_purecall_handler**函数，**则_purecall**函数将调用该函数。 可以安装自己的错误处理程序进行纯虚拟函数调用，以捕获这些调用用于调试和报告目的。 要使用自己的错误处理程序，请创建具有 **_purecall_handler**签名的函数，然后使用[_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)使其成为当前处理程序。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

**_purecall**函数没有标头声明。 **_purecall_handler**类型def在 stdlib.h>中\<定义。

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler、_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
