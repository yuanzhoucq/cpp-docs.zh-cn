---
title: "编译器警告 （等级 4） C4960 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4960
dev_langs:
- C++
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 63849c73ffb96038058582b6cdc2519620290ccd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4960"></a>编译器警告（等级 4）C4960
“function”太大，无法配置  
  
 当使用 [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)时，编译器检测到某个输入模块的函数具有的指令超过 65,535 条。 如此大的函数不可用于按配置进行的优化。  
  
 若要解决此警告，请减小该函数的大小。