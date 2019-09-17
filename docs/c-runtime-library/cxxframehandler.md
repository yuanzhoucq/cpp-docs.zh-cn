---
title: __CxxFrameHandler
ms.date: 11/04/2016
api_name:
- __CxxFrameHandler
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __CxxFrameHandler
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
ms.openlocfilehash: 4cb5ae10d4281c4a7167db7adf4ea6788ad3e3c0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944503"
---
# <a name="__cxxframehandler"></a>__CxxFrameHandler

内部 CRT 函数。 由 CRT 用于处理结构化异常帧。

## <a name="syntax"></a>语法

```cpp
EXCEPTION_DISPOSITION __CxxFrameHandler(
      EHExceptionRecord  *pExcept,
      EHRegistrationNode *pRN,
      void               *pContext,
      DispatcherContext  *pDC
   )
```

#### <a name="parameters"></a>参数

*pExcept*<br/>
传递给可能的 `catch` 语句的异常记录。

*pRN*<br/>
有关用于处理异常的堆栈帧的动态信息。 有关详细信息，请参阅 ehdata.h。

*pContext*<br/>
上下文。 （不可用于 Intel 处理器上。）

*pDC*<br/>
有关函数入口和堆栈帧的其他信息。

## <a name="return-value"></a>返回值

由 [try-except 语句](../cpp/try-except-statement.md)使用的 filter expression  值之一。

## <a name="remarks"></a>备注

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|__CxxFrameHandler|excpt.h，ehdata.h|