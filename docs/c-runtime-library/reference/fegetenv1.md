---
title: fegetenv |Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fetegenv
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
- fegetenv
- fenv/fegetenv
dev_langs:
- C++
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc8b5d189838c2788bc6200f9072c9511e61d42f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fegetenv"></a>fegetenv

在指定对象中存储当前浮点环境。

## <a name="syntax"></a>语法

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>参数

*penv*<br/>
指向**fenv_t**对象，以包含当前的浮点环境值。

## <a name="return-value"></a>返回值

如果成功，浮点环境时存储在返回 0 *penv*。 否则，返回一个非零值。

## <a name="remarks"></a>备注

**Fegetenv**函数将当前的浮点环境存储在通过指向的对象*penv*。 浮点环境是一系列影响浮点计算的状态标志和控件模式。 包括舍入方向模式和浮点异常的状态标志。  如果*penv*不指向有效**fenv_t**对象，后续的行为是不确定。

若要使用此函数，必须在调用前先使用 `#pragma fenv_access(on)` 指令关闭可能会阻止访问的浮点优化。 有关详细信息，请参阅 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
