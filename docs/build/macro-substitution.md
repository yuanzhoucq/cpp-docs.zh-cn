---
title: 宏替换 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4028ee710cf38b6a4ef929de9a7e4ffad95f3e41
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368065"
---
# <a name="macro-substitution"></a>宏替换
当*macroname*调用时，每个匹配项*string1*字符串由其定义中的替换*string2*。  
  
## <a name="syntax"></a>语法  
  
```  
$(macroname:string1=string2)  
```  
  
## <a name="remarks"></a>备注  
 宏替换是区分大小写，文本;*string1*和*string2*无法调用宏。 替换不会修改原始定义。 你可以替换文本中除之外的任何预定义宏[ $$@ ](../build/filename-macros.md)。  
  
 冒号; 上前面均不包含空格或选项卡任何冒号后面都会被解释为文本。 如果*string2*是 null，出现的所有*string1*宏的定义字符串中删除。  
  
## <a name="see-also"></a>请参阅  
 [使用 NMAKE 宏](../build/using-an-nmake-macro.md)