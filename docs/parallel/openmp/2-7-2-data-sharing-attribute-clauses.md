---
title: "2.7.2 数据共享特性子句 |Microsoft 文档"
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
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c63ece0feea0426fffbafa600f578e342e85fc2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 数据共享特性子句
多个指令接受允许用户控制变量的共享属性区域的持续时间内的子句。 共享特性子句仅适用于子句在其显示的指令的词法范围中的变量。 并非所有以下子句可以在所有指令。 指令一起描述了在特定指令都有效的子句的列表。  
  
 如果变量是可见时并行或遇到工作共享构造，并且不在共享特性子句中指定变量或**threadprivate**指令，然后变量共享的。 共享并行区域的动态范围内声明的静态变量。 堆分配的内存 (例如，使用**malloc()** C 或 c + + 或**新**c + + 中的运算符) 共享。 （指向此内存，但是，可以是专用或共享。）具有自动存储持续时间在并行区域的动态范围内声明的变量是私有类型。  
  
 子句的大多数接受*变量列表*自变量，这是可见的变量的以逗号分隔列表。 如果变量引用中的数据共享特性子句已从模板派生的类型并且不有与该变量在程序中的任何其他引用，该行为不确定。  
  
 在指令子句内出现的所有变量必须都是可见的。 可能重复子句，根据需要但可能在多个子句中，指定任何变量，只不过可以中同时指定变量**firstprivate**和**lastprivate**子句。  
  
 下列各节描述数据共享特性子句：  
  
-   **私有**，[部分 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)第 25 页上。  
  
-   **firstprivate**，[部分 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md)在页上 26。  
  
-   **lastprivate**，[部分 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md)第 27 页上。  
  
-   **共享**，[部分 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md)第 27 页上。  
  
-   **默认**，[部分 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md)第 28 页上。  
  
-   **减少**，[部分 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md)第 28 页上。  
  
-   **copyin**，[部分 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md)第 31 页。  
  
-   **copyprivate**，[部分 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md)在页上 32。