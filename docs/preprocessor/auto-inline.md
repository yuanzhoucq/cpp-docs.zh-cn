---
title: auto_inline
ms.date: 11/04/2016
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: a3e49941271ec294ddb69861d12e3451332770fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633334"
---
# <a name="autoinline"></a>auto_inline
排除范围内定义的所有函数其中**关闭**从正在被视为候选项为自动内联扩展中指定。

## <a name="syntax"></a>语法

```
#pragma auto_inline( [{on | off}] )
```

## <a name="remarks"></a>备注

若要使用**auto_inline**杂注时，将其放置在之前和之后立即 （不在） 函数定义。 杂注在出现的位置后的第一个函数定义处生效。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)