---
title: 2.6.2 critical 构造 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae7070fcc590307e71b0c34259bcbe1c12200550
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="262-critical-construct"></a>2.6.2 critical 构造
**关键**指令标识一个构造，用于限制为单线程的执行关联的结构化块，一次。 语法**关键**指令是，如下所示：  
  
```  
#pragma omp critical [(name)]  new-linestructured-block  
```  
  
 一个可选*名称*可用于标识的关键区域。 用于标识关键区域的标识符具有外部链接，且处于这不同于使用的标签、 标记、 成员和普通标识符的命名空间的命名空间。  
  
 关键区域的开始处的一个线程等待，直到没有其他线程执行 （任意位置中程序） 具有相同名称的一个关键区域。 所有未命名**关键**指令映射到相同的未指定名称。