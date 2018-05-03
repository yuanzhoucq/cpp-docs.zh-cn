---
title: 参数访问 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: article
f1_keywords:
- c.arguments
dev_langs:
- C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afef1300637f7a31755eb9408f9d33d9504475a1
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
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
