---
title: __uncaught_exception
ms.date: 11/04/2016
apiname:
- __uncaught_exception
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
apitype: DLLExport
f1_keywords:
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 19d1e18af27722d6f9da39ebaaf6c9415c281849
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268892"
---
# <a name="uncaughtexception"></a>__uncaught_exception

指示是否已抛出一个或多个异常，但未处理的相应**捕获**块[try catch](../../cpp/try-throw-and-catch-statements-cpp.md)语句。

## <a name="syntax"></a>语法

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>返回值

**true**从时将引发异常**尝试**块，直到匹配**catch**块已初始化; 否则为**false**。

## <a name="remarks"></a>备注

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>请参阅

[try、throw 和 catch 语句 (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
