---
title: ML 非致命错误 A2085 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd5ec9f36a4f956b8eeb097b6a8f8eaed89ba2b2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681430"
---
# <a name="ml-nonfatal-error-a2085"></a>ML 非致命错误 A2085

**指令或不接受当前 CPU 模式下的注册**

尝试使用指令、 寄存器或对当前处理器模式下无效的关键字。

例如，需要 32 位寄存器[.386](../../assembler/masm/dot-386.md)或更高版本。 如 CR0 需要特权模式下，控制寄存器[.386P](../../assembler/masm/dot-386p.md)或更高版本。 此错误也会生成有关**NEAR32**， **FAR32**，并**平面**要求的关键字。**386**或更高版本。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>