---
title: 宏替换 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f71ef2e1a8f337a4cd415169b6f9d817042f19a
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894390"
---
# <a name="macro-substitution"></a>宏替换

当*macroname*调用时，出现的每个*string1*在其定义中字符串被替换为*string2*。

## <a name="syntax"></a>语法

```
$(macroname:string1=string2)
```

## <a name="remarks"></a>备注

宏替换区分大小写，是文本;*string1*并*string2*不能调用宏。 替换不会修改原始定义。 你可以替换文本中除任何预定义的宏[ $$@ ](../build/filename-macros.md)。

空格或制表符前加上冒号;任何冒号后被解释为文本。 如果*string2*为 null 的所有匹配项*string1*宏的定义字符串中删除。

## <a name="see-also"></a>请参阅

[使用 NMAKE 宏](../build/using-an-nmake-macro.md)