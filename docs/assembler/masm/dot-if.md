---
title: .IF | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .IF
dev_langs:
- C++
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7bd5ba5821b4dcfb2d088e31816f50540445018
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691539"
---
# <a name="if"></a>.IF

生成测试的代码`condition1`(例如，AX > 7)，并执行*语句*如果该条件为 true。

## <a name="syntax"></a>语法

> .如果 condition1<br/>
> 语句<br/>
> [[.ELSEIF condition2<br/>
> 语句]]<br/>
> [[.其他<br/>
> 语句]]<br/>
> .ENDIF

## <a name="remarks"></a>备注

如果[。其他](../../assembler/masm/dot-else.md)当原始的条件为 false，如下所示，其语句才执行。 请注意在运行时计算条件。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>