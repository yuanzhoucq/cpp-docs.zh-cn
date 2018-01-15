---
title: "ML 非致命错误 A2096 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2096
dev_langs: C++
helpviewer_keywords: A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d4466d87e33068b10b3f620bfbe764e4aec76c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2096"></a>ML 非致命错误 A2096
**段、 组或预期的段寄存器**  
  
 段或组应但未找到。  
  
 出现以下之一：  
  
-   左的操作数指定使用了段重写运算符 (**:**) 未段寄存器 （CS、 DS、 SS、 ES、 FS 或 GS），组名、 段名称或段表达式。  
  
-   [假定](../../assembler/masm/assume.md)指令提供而不是有效的段地址、 段寄存器，组中或这两个特殊的段寄存器**平面**组。  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)