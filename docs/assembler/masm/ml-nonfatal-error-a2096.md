---
title: ML 非致命错误 A2096 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2096
dev_langs:
- C++
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f4ef76dca10b1208a931bc3e1cc09d82a639d2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679593"
---
# <a name="ml-nonfatal-error-a2096"></a>ML 非致命错误 A2096

**段、 组或预期的段寄存器**

段或组应，但找不到。

出现下列情况之一：

- 左的操作数指定的段重写运算符 (**:**) 段寄存器 （CS、 DS、 SS、 ES、 FS 中或 GS），组名、 段名称或段表达式不是。

- [ASSUME](../../assembler/masm/assume.md)指令提供的段寄存器，而无需有效段地址、 段注册、 组或这两个特殊**平面**组。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>