---
title: __uncaught_exception | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcae75a5d25710866f781d766cfd77eceb977649
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408210"
---
# <a name="uncaughtexception"></a>__uncaught_exception

指示是否一个或多个异常已抛出，但尚未处理相应**捕获**块[try catch](../../cpp/try-throw-and-catch-statements-cpp.md)语句。

## <a name="syntax"></a>语法

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>返回值

**true**从时将引发异常**重**直到相匹配的块**捕获**块是初始化; 否则为**false**。

## <a name="remarks"></a>备注

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>请参阅

[try、throw 和 catch 语句 (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
