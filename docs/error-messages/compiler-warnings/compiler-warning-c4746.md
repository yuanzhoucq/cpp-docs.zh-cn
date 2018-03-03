---
title: "编译器警告 C4746 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f92bae0e75d9a09de874cd999c044e703b3f3171
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4746"></a>编译器警告 C4746
可变访问\<表达式 > 受 /volatile: [iso &#124; ms] 设置; 请考虑使用 __iso_volatile_load/store 内部函数。  
  
 直接访问可变变量时会发出 C4746。 它旨在帮助开发人员标识受当前指定的特定可变模型的代码位置 (这可以控制与[/易失性](../../build/reference/volatile-volatile-keyword-interpretation.md)编译器选项)。 具体而言，如果要在使用 /volatile:ms 时查找编译器生成的硬件内存屏障，它很有用。  
  
 __iso_volatile_load/store 内部函数可用于显式访问可变内存而不会受可变模型的影响。 使用这些内部函数不会触发 C4746。  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。