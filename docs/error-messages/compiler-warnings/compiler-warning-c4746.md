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
caps.latest.revision: 2
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 1b88f51aa9365c0795c8d3d944ba9f3a8db059d9
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-c4746"></a>编译器警告 C4746
可变访问\<表达式 > 受 /volatile: [iso &#124; ms] 设置; 请考虑使用 __iso_volatile_load/store 内部函数。  
  
 直接访问可变变量时会发出 C4746。 它旨在帮助开发人员标识受当前指定的特定可变模型的代码位置 (这可以控制与[/易失性](../../build/reference/volatile-volatile-keyword-interpretation.md)编译器选项)。 具体而言，如果要在使用 /volatile:ms 时查找编译器生成的硬件内存屏障，它很有用。  
  
 __iso_volatile_load/store 内部函数可用于显式访问可变内存而不会受可变模型的影响。 使用这些内部函数不会触发 C4746。  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。
