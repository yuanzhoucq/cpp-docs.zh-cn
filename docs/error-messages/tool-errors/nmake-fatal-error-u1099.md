---
title: "NMAKE 错误 U1099 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1099
dev_langs: C++
helpviewer_keywords: U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e84cb96fdc8b3abfa118d653162e40c90683447a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 错误 U1099
堆栈溢出  
  
 生成文件中正在处理已过于复杂，NMAKE 中的当前堆栈分配。 NMAKE 具有 0x3000 (12 K) 分配。  
  
 若要增加 NMAKE 的堆栈分配，运行[editbin /stack](../../build/reference/stack.md)实用工具使用更大的堆栈选项：  
  
 **editbin /STACK:reserve NMAKE。EXE**  
  
 其中*保留*是一个数字大于 NMAKE 中的当前堆栈分配。