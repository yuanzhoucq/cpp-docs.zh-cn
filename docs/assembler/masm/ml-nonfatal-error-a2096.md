---
title: ML 非致命错误 A2096
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: 14fb30214cf7badf51368672dc52635d50a067f1
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855469"
---
# <a name="ml-nonfatal-error-a2096"></a>ML 非致命错误 A2096

**应输入段、组或段寄存器**

需要段或组，但找不到。

出现下列情况之一：

- 使用段替代运算符（ **：** ）指定的左操作数不是段寄存器（CS、DS、SS、ES、FS 或 GS）、组名称、段名称或段表达式。

- [假设](../../assembler/masm/assume.md)在给定段寄存器时没有有效的段地址、段寄存器、组或特殊的**平面**组。

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>