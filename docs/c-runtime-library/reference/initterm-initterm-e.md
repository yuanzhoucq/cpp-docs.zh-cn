---
title: _initterm、_initterm_e
ms.date: 11/04/2016
api_name:
- _initterm_e
- _initterm
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
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _initterm_e
- initterm
- _initterm
- initterm_e
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
ms.openlocfilehash: 7e85494bf6c8215d03602ee112e1ff2c0f1cf6f2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954621"
---
# <a name="_initterm-_initterm_e"></a>_initterm、_initterm_e

用于访问函数指针表并将其初始化的内部方法。

第一个指针位于表中的起始位置，第二个指针位于结束位置。

## <a name="syntax"></a>语法

```C
void __cdecl _initterm(
   PVFV *,
   PVFV *
);

int __cdecl _initterm_e(
   PVFV *,
   PVFV *
);
```

## <a name="return-value"></a>返回值

如果初始化失败并引发错误，则返回一个非零的错误代码；如果未发生错误，则返回 0。

## <a name="remarks"></a>备注

这些方法只能在 C++ 程序的初始化过程中进行内部调用。 请勿在程序中调用这些方法。

当这些方法遍历函数项的表时，它们会跳过**空**项，然后继续。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
