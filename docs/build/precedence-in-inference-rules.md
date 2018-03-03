---
title: "推理规则中的优先级 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f7374da0541fc66464947af5a7b2ea7ea7b5c1d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="precedence-in-inference-rules"></a>推理规则中的优先级
如果有多个定义推理规则，NMAKE 使用优先级最高的定义。 以下列表显示优先级从高到最低的顺序：  
  
1.  生成文件; 中定义的推理规则更高版本定义具有优先级。  
  
2.  Tools.ini; 中定义的推理规则更高版本定义具有优先级。  
  
3.  预定义的推理规则。  
  
## <a name="see-also"></a>请参阅  
 [推理规则](../build/inference-rules.md)