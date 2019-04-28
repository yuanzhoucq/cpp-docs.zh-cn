---
title: ML 非致命错误 A2096
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: e6b31afeff801e7128b5a76576e9eaa3398f68e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62202485"
---
# <a name="ml-nonfatal-error-a2096"></a>ML 非致命错误 A2096

**段、 组或预期的段寄存器**

段或组应，但找不到。

出现下列情况之一：

- 左的操作数指定的段重写运算符 (**:**) 段寄存器 （CS、 DS、 SS、 ES、 FS 中或 GS），组名、 段名称或段表达式不是。

- [ASSUME](../../assembler/masm/assume.md)指令提供的段寄存器，而无需有效段地址、 段注册、 组或这两个特殊**平面**组。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>