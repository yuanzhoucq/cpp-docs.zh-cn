---
title: 推理规则中的优先级 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36d462d4222cbfc143dd7487d4cb6b1b8bb3ba3b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368481"
---
# <a name="precedence-in-inference-rules"></a>推理规则中的优先级
如果有多个定义推理规则，NMAKE 使用优先级最高的定义。 以下列表显示优先级从高到最低的顺序：  
  
1.  生成文件; 中定义的推理规则更高版本定义具有优先级。  
  
2.  Tools.ini; 中定义的推理规则更高版本定义具有优先级。  
  
3.  预定义的推理规则。  
  
## <a name="see-also"></a>请参阅  
 [推理规则](../build/inference-rules.md)