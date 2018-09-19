---
title: .堆栈 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95e8d69903fabf60fdb5bc04d90452bdad163a19
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676231"
---
# <a name="stack"></a>.STACK

与一起使用时[。模型](../../assembler/masm/dot-model.md)，定义一个堆栈段 （使用段名称堆栈）。 可选`size`指定的堆栈 （默认值为 1024） 的字节数。 `.STACK`指令会自动关闭堆栈语句。

## <a name="syntax"></a>语法

> .堆栈 [[size]]

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>