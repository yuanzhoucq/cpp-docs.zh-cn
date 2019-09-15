---
title: _purecall
ms.date: 11/04/2016
api_name:
- _purecall
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
ms.openlocfilehash: 5d62ec30731ce26c4683afc88474d4bddb63a697
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950155"
---
# <a name="_purecall"></a>_purecall

默认纯虚拟函数调用错误处理程序。 当调用纯虚拟成员函数时，编译器生成调用此函数的代码。

## <a name="syntax"></a>语法

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>备注

**_Purecall**函数是 microsoft C++编译器的特定于 microsoft 的实现细节。 此函数不可以直接通过代码调用，也没有任何公用标头声明。 之所以在这里讨论此函数，是因为它是 C 运行时库的公用导出。

对纯虚拟函数的调用出错，因为它没有实现。 调用纯虚函数时，编译器将生成代码来调用 **_purecall**错误处理程序函数。 默认情况下， **_purecall**将终止该程序。 在终止之前， **_purecall**函数会调用 **_purecall_handler**函数（如果已为进程设置了一个函数）。 可以安装自己的错误处理程序进行纯虚拟函数调用，以捕获这些调用用于调试和报告目的。 若要使用自己的错误处理程序，请创建具有 **_purecall_handler**签名的函数，然后使用[_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)使其成为当前处理程序。

## <a name="requirements"></a>要求

**_Purecall**函数没有标头声明。 **_Purecall_handler** typedef 是在 stdlib.h > \<中定义的。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler、_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
