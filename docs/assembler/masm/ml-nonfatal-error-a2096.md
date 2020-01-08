---
title: ML 非致命错误 A2096
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: 425e99c1dc6675e8b970433948e0cc09b8d54485
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312659"
---
# <a name="ml-nonfatal-error-a2096"></a>ML 非致命错误 A2096

**应输入段、组或段寄存器**

需要段或组，但找不到。

出现下列情况之一：

- 使用段替代运算符（ **：** ）指定的左操作数不是段寄存器（CS、DS、SS、ES、FS 或 GS）、组名称、段名称或段表达式。

- [假设](assume.md)在给定段寄存器时没有有效的段地址、段寄存器、组或特殊的**平面**组。

## <a name="see-also"></a>另请参阅

[ML 错误消息](ml-error-messages.md)
