---
title: 参数访问
ms.date: 04/04/2018
f1_keywords:
- c.arguments
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
ms.openlocfilehash: 8107cffa6a2da41c38b116b2e3fe36adf6ac945f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470403"
---
# <a name="argument-access"></a>参数访问

当参数数量可变时，va_arg、va_end 和 va_start 宏提供对函数参数的访问。 为了兼容 ANSI/ISO C，\<stdarg.h> 中定义了这些宏。为了兼容 UNIX System V，\<varargs.h> 中定义了这些宏。

## <a name="argument-access-macros"></a>参数-访问宏

|宏|使用|
|-----------|-------------------------------|
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|从列表中检索自变量|
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|重置指针|
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|将指针设置到自变量列表的开始位置|

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)
