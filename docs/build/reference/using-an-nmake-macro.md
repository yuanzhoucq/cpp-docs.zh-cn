---
title: 使用 NMAKE 宏
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: fb3b154ba8b30bbfc9a6c7c6b37720e5c60d6327
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825048"
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

[宏替换](macro-substitution.md)

## <a name="see-also"></a>请参阅

[宏和 NMAKE](macros-and-nmake.md)
