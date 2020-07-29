---
title: _abnormal_termination
ms.date: 11/04/2016
api_name:
- _abnormal_termination
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: a963f1059eccaddce9ec01cd53a07df668ee46c6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213653"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

指示 **`__finally`** 当系统正在执行终止处理程序的内部列表时，是否输入[try-catch 语句](../cpp/try-finally-statement.md)的块。

## <a name="syntax"></a>语法

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>返回值

**`true`** 如果系统正在*展开*堆栈，则为;否则为 **`false`** 。

## <a name="remarks"></a>备注

这是用于管理展开异常的内部函数，并且不应从用户代码调用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>请参阅

[try-finally 语句](../cpp/try-finally-statement.md)
