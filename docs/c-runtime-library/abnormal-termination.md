---
title: _abnormal_termination |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _abnormal_termination
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _abnormal_termination
dev_langs:
- C++
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e311c27d61eca82019f8069b0984557af02c74a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028202"
---
# <a name="abnormaltermination"></a>_abnormal_termination

指示是否在系统执行终止处理程序的内部列表时进入 [try-finally 语句](../cpp/try-finally-statement.md)的 `__finally` 块。

## <a name="syntax"></a>语法

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>返回值

如果系统*展开*堆栈，则为 `true`；否则为 `false`。

## <a name="remarks"></a>备注

这是用于管理展开异常的内部函数，并且不应从用户代码调用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>请参阅

[try-finally 语句](../cpp/try-finally-statement.md)