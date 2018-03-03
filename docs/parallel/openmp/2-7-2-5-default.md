---
title: "2.7.2.5 默认 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ee328be7f9f0c4876738f8179c26e700c57702c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="2725-default"></a>2.7.2.5 default
**默认**子句允许用户会影响变量的数据共享特性。 语法**默认**子句是，如下所示：  
  
```  
default(shared | none)  
```  
  
 指定**default(shared)**等效于显式列出在每个当前可见变量**共享**子句，除非它是**threadprivate**或**cons**`t`-限定。 在没有显式**默认**默认行为是相同的子句，如果**default(shared)**指定。  
  
 指定**default(none)**需要至少一个以下必须满足每个引用中的并行构造的词法范围的变量：  
  
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