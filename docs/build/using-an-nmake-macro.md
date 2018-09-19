---
title: 使用 NMAKE 宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0b68a5f3128b5d3780895f8080411819ed9b538
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712573"
---
# <a name="using-an-nmake-macro"></a>使用 NMAKE 宏

若要使用宏，用括起来，如下所示后面美元符号 （$） 的括号中。

## <a name="syntax"></a>语法

```
$(macroname)
```

## <a name="remarks"></a>备注

不允许有空格。 括号是可选的如果*macroname*是单个字符。 定义字符串将替换 $(*macroname*); 未定义的宏替换为空字符串。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[宏替换](../build/macro-substitution.md)

## <a name="see-also"></a>请参阅

[宏和 NMAKE](../build/macros-and-nmake.md)