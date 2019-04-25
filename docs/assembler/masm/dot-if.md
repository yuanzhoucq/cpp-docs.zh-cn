---
title: .IF
ms.date: 08/30/2018
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: cf9c594d843c937dd2191bee2a7cebadbc615c82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62185261"
---
# <a name="if"></a>.IF

生成测试的代码`condition1`(例如，AX > 7)，并执行*语句*如果该条件为 true。

## <a name="syntax"></a>语法

> .如果 condition1<br/>
> 语句<br/>
> [[.ELSEIF condition2<br/>
> 语句]]<br/>
> [[.ELSE<br/>
> 语句]]<br/>
> .ENDIF

## <a name="remarks"></a>备注

如果[。其他](../../assembler/masm/dot-else.md)当原始的条件为 false，如下所示，其语句才执行。 请注意在运行时计算条件。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>