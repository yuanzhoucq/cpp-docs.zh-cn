---
title: 编译器警告 （等级 4） C4960 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4960
dev_langs:
- C++
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1281bc86ad363c02df5c39ed41f616a6fff1a9b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294422"
---
# <a name="compiler-warning-level-4-c4960"></a>编译器警告（等级 4）C4960
“function”太大，无法配置  
  
 当使用 [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)时，编译器检测到某个输入模块的函数具有的指令超过 65,535 条。 如此大的函数不可用于按配置进行的优化。  
  
 若要解决此警告，请减小该函数的大小。