---
title: TZNAME_MAX | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- TZNAME_MAX
dev_langs:
- C++
helpviewer_keywords:
- TZNAME_MAX constant
ms.assetid: e2286cb8-751d-4557-9650-5c4b98a8f7be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc44ff3178493132c1b8d5dc168cee6be4c5bc56
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990147"
---
# <a name="tznamemax"></a>TZNAME_MAX

**已过时**。 时区名称变量允许的最大字符串长度。 Visual Studio 2012 和早期版本中的 \<limits.h> 定义了此宏。 Visual Studio 2013 及更高版本中未定义它。 要获取保存当前时区名称所需的长度，请使用 [_get_tzname](../c-runtime-library/reference/get-tzname.md)。

## <a name="syntax"></a>语法

```
#include <limits.h>
```

## <a name="see-also"></a>请参阅

[环境常量](../c-runtime-library/environmental-constants.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)
