---
title: ML 非致命错误 A2096 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6e5d07afa864c9f6f4214de953aa9e03fe0e7e4f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053667"
---
# <a name="ml-nonfatal-error-a2096"></a>ML 非致命错误 A2096
**段、 组或预期的段寄存器**  
  
 段或组应但未找到。  
  
 出现以下之一：  
  
-   左的操作数指定使用了段重写运算符 (**:**) 未段寄存器 （CS、 DS、 SS、 ES、 FS 或 GS），组名、 段名称或段表达式。  
  
-   [假定](../../assembler/masm/assume.md)指令提供而不是有效的段地址、 段寄存器，组中或这两个特殊的段寄存器**平面**组。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)