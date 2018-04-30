---
title: 联合 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- union
dev_langs:
- C++
helpviewer_keywords:
- UNION directive
ms.assetid: 52504abf-7dc1-47c5-944c-b886803a0c6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71a2d7644e14903d2c4a9c4191ce54c8fea14849
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="union"></a>UNION
声明的一个或多个数据类型的联合。 *Fielddeclarations*必须是有效的数据定义。 省略[结束](../../assembler/masm/ends-masm.md)*名称*上的标签嵌套**联合**定义。  
  
## <a name="syntax"></a>语法  
  
```  
  
      name   
      UNION [[alignment]] [[, NONUNIQUE]]  
   fielddeclarations  
[[name]] ENDS  
```  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)