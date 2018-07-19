---
title: 2.7.2.3 lastprivate |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08f331862d6e48b1c0882382285ddffa9699e79c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687337"
---
# <a name="2723-lastprivate"></a>2.7.2.3 lastprivate
`lastprivate`子句提供的提供的功能超集`private`子句。 语法`lastprivate`子句是，如下所示：  
  
```  
lastprivate(variable-list)  
```  
  
 中指定的变量*变量列表*具有`private`子句语义。 当`lastprivate`标识工作共享构造，每个值的指令上出现子句`lastprivate`的关联的循环或部分包含的词法上最后一个指令，按顺序最后一次迭代中的变量分配给变量的原始对象。 不是变量值分配到的最后一次迭代**为**或**并行的**，或通过的词法上最后一节**部分**或**并行部分**指令，则构造之后，具有不确定的值。 之后构造，未分配的子对象也具有不确定的值。  
  
 对限制`lastprivate`子句如下所示：  
  
-   所有限制`private`应用。  
  
-   具有指定为类类型的变量`lastprivate`必须具有可访问的明确复制赋值运算符。  
  
-   变量的是专用的并行区域内或出现在`reduction`子句**并行**指令不能指定`lastprivate`将绑定到并行构造工作共享指令上的子句。