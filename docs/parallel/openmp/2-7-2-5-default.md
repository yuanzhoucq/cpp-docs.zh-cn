---
title: 2.7.2.5 默认 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c054c7f0ac7d1d73768d84613524afc979fecaa5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="2725-default"></a>2.7.2.5 default
**默认**子句允许用户会影响变量的数据共享特性。 语法**默认**子句是，如下所示：  
  
```  
default(shared | none)  
```  
  
 指定**default(shared)** 等效于显式列出在每个当前可见变量**共享**子句，除非它是**threadprivate**或**cons**`t`-限定。 在没有显式**默认**默认行为是相同的子句，如果**default(shared)** 指定。  
  
 指定**default(none)** 需要至少一个以下必须满足每个引用中的并行构造的词法范围的变量：  
  
-   该变量显式列出一个构造，用于包含引用的数据共享特性子句中。  
  
-   并行构造中声明变量。  
  
-   变量是**threadprivate**。  
  
-   该变量具有**const**-限定类型。  
  
-   变量是为循环控制变量**为**紧随的循环**为**或**为并行**循环内将出现指令和变量的引用.  
  
 指定一个变量上**firstprivate**， **lastprivate**，或**缩减**封闭指令子句导致为变量的隐式引用封闭上下文。 这种隐式引用也受到上面列出的要求。  
  
 只有一个**默认**子句可指定在**并行**指令。  
  
 可以使用替代数据共享特性的变量的默认**私有**， **firstprivate**， **lastprivate**，**缩减**，和**共享**子句，如下面的示例所示：  
  
```  
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\  
   private(x)  private(r)  lastprivate(i)  
```