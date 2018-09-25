---
title: FOPEN_MAX、_SYS_OPEN | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _SYS_OPEN
- FOPEN_MAX
dev_langs:
- C++
helpviewer_keywords:
- SYS_OPEN constant
- _SYS_OPEN constant
- FOPEN_MAX constant
- files [C++], maximum open
- maximum number of files
- open files, maximum
ms.assetid: 39cf5196-250a-459d-ae90-ce3d99f79039
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18653eaae84e619e549146bd721dee3199f90ac5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090888"
---
# <a name="fopenmax-sysopen"></a>FOPEN_MAX、_SYS_OPEN

## <a name="syntax"></a>语法

```

#include <stdio.h>

```

## <a name="remarks"></a>备注

这是可同时打开的文件的最大数目。 `FOPEN_MAX` 是与 ANSI 兼容的名称。 提供 `_SYS_OPEN` 以便与现有代码兼容。

## <a name="see-also"></a>请参阅

[全局常量](../c-runtime-library/global-constants.md)