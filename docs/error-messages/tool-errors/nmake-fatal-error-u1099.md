---
title: NMAKE 错误 U1099 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1099
dev_langs:
- C++
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7be09691de4212d07b1452ffe33725a3978fc053
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322099"
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE 错误 U1099
堆栈溢出  
  
 生成文件中正在处理已过于复杂，NMAKE 中的当前堆栈分配。 NMAKE 具有 0x3000 (12 K) 分配。  
  
 若要增加 NMAKE 的堆栈分配，运行[editbin /stack](../../build/reference/stack.md)实用工具使用更大的堆栈选项：  
  
 **editbin /STACK:reserve NMAKE。EXE**  
  
 其中*保留*是一个数字大于 NMAKE 中的当前堆栈分配。