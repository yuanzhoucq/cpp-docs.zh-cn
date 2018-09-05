---
title: .重复 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .REPEAT
dev_langs:
- C++
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8856ed0e1d86277a413baac2c56e5c5ca2ea9ff0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687947"
---
# <a name="repeat"></a>.REPEAT

生成重复的块执行的代码*语句*直到`condition`而变为 true。 [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)，这将为 true 时 CX 为零，可能会替换为[。直到](../../assembler/masm/dot-until.md)。 `condition`是可选的 **。UNTILCXZ**。

## <a name="syntax"></a>语法

> .REPEAT<br/>
> 语句<br/>
> .UNTIL 条件

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>