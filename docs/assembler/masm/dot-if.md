---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 83c9ff588e2fe273e24e1d0b1c16517c5eee3365
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703786"
---
# <a name="if-32-bit-masm"></a>.IF （32位 MASM）

生成测试 `condition1` （例如，AX > 7）的代码，如果该条件为 true，则执行*语句*。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> .如果 condition1<br/>
> 语句<br/>
> [[.ELSEIF condition2<br/>
> 语句]]<br/>
> [[.其它<br/>
> 语句]]<br/>
> .ENDIF

## <a name="remarks"></a>备注

如果为[。否则](../../assembler/masm/dot-else.md)，如果原始条件为 false，则执行其语句。 请注意，将在运行时评估条件。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>