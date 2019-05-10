---
title: _purecall
ms.date: 11/04/2016
apiname:
- _purecall
apilocation:
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
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: df6dde91ccb952e66eb77c841b2b1ace12756b8c
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446626"
---
# <a name="purecall"></a>_purecall

默认纯虚拟函数调用错误处理程序。 当调用纯虚拟成员函数时，编译器生成调用此函数的代码。

## <a name="syntax"></a>语法

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>备注

**_Purecall**函数是 Microsoft 的特定于 Microsoft 的实现详细信息C++编译器。 此函数不可以直接通过代码调用，也没有任何公用标头声明。 之所以在这里讨论此函数，是因为它是 C 运行时库的公用导出。

对纯虚拟函数的调用出错，因为它没有实现。 编译器生成代码以调用 **_purecall**错误处理程序函数调用纯虚函数时。 默认情况下 **_purecall**终止程序。 在终止之前， **_purecall**函数将调用 **_purecall_handler 中**函数如果已设置了一个进程。 可以安装自己的错误处理程序进行纯虚拟函数调用，以捕获这些调用用于调试和报告目的。 若要使用错误处理程序，创建具有的函数 **_purecall_handler 中**签名，然后使用[_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)使它成为当前处理程序。

## <a name="requirements"></a>要求

**_Purecall**函数没有标头声明。 **_Purecall_handler 中**中定义 typedef \<stdlib.h >。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler、_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
