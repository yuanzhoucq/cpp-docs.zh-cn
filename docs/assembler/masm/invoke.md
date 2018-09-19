---
title: 调用 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Invoke
dev_langs:
- C++
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e5698acf9986903a1d6d731c1047484a0ce6904
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676512"
---
# <a name="invoke"></a>INVOKE

在给定的地址调用该过程*表达式*，将自变量传递到堆栈上或在寄存器中根据语言类型的标准调用约定。

## <a name="syntax"></a>语法

> INVOKE*表达式*[[，*自变量*]]

## <a name="remarks"></a>备注

每个自变量传递给该过程可能是表达式、 是注册的对或地址表达式 (表达式前面`ADDR`)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>