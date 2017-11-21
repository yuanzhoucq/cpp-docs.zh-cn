---
title: "1.4 法规遵从性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8481c0efb54a397db004f321fb48c217cba8ebc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="14-compliance"></a>1.4 遵从性
OpenMP C/c + + API 的实现是*OpenMP 符合*如果它识别，并保留本规范的所有元素的语义，如按章节 1、 2、 3、 4、 布局和附录 c。 附录 A、 B、 D、 E 和 F 适用于信息仅目的并不规范的一部分。 仅包含一个子集的 api 的实现都不是 OpenMP 符合。  
  
 OpenMP C 和 c + + API 是支持的实现的基本语言的扩展。 如果基本语言不支持此文档中的语言构造或扩展，将出现，OpenMP 实现不需要支持它。  
  
 所有标准的 C 和 c + + 库函数和内置函数 （即，编译器具有特定知识的函数） 必须是线程安全的。 未同步的使用不同的线程并行区域内的线程安全函数不会产生未定义的行为。 但是，行为可能不是与串行区域中的相同。 （随机数生成函数是一个示例。）  
  
 OpenMP C/c + + API 指定某些行为是*实现定义。* 需要定义并记录在这些情况下其行为是一致的 OpenMP 实现。 请参阅[附录 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md)，页上 97，为实现定义的行为的列表。