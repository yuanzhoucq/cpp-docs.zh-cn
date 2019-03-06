---
title: 宏替换
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
ms.openlocfilehash: d82aed5a34b7cafad0e40146470972dc6ff02424
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414676"
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
