---
title: ___setlc_active_func、___unguarded_readlc_active_add_func | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
dev_langs:
- C++
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59ec444ae81d680bf57aa4542f231c021f1abddc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102771"
---
# <a name="setlcactivefunc-unguardedreadlcactiveaddfunc"></a>___setlc_active_func、___unguarded_readlc_active_add_func

已过时。 CRT 仅导出这些内部函数以保留二进制兼容性。

## <a name="syntax"></a>语法

```cpp
int ___setlc_active_func(void);
int * ___unguarded_readlc_active_add_func(void);
```

## <a name="return-value"></a>返回值

返回的值不重要。

## <a name="remarks"></a>备注

尽管内部 CRT 函数 `___setlc_active_func` 和 `___unguarded_readlc_active_add_func` 已过时且不再使用，但是 CRT 库还会导出它们以保留二进制兼容性。 `___setlc_active_func` 的原始用途是返回对 `setlocale` 函数的当前活动的调用数。 `___unguarded_readlc_active_add_func` 的原始用途是返回引用区域设置而不会锁定区域设置的函数数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|无|

## <a name="see-also"></a>请参阅

[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)