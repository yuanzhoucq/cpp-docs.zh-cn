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
ms.openlocfilehash: b66cf0df998b4e33a9f3425fdf0f260d163f423b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944715"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

指示是否在系统执行终止处理程序的内部列表时进入 [try-finally 语句](../cpp/try-finally-statement.md)的 `__finally` 块。

## <a name="syntax"></a>语法

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>返回值

如果系统“展开”堆栈则为“true”，否则为“false”    。

## <a name="remarks"></a>备注

这是用于管理展开异常的内部函数，并且不应从用户代码调用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>请参阅

[try-finally 语句](../cpp/try-finally-statement.md)
