---
title: _initterm, _initterm_e | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _initterm_e
- _initterm
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
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _initterm_e
- initterm
- _initterm
- initterm_e
dev_langs:
- C++
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 470ad6cbf13efb170f61aa12f7859f2baa248c2b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="initterm-initterme"></a>_initterm、_initterm_e

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

当这些方法访问函数条目表时，它们会跳过**NULL**条目并继续。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
