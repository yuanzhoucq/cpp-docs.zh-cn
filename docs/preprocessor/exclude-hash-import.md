---
title: "排除 (#import) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: exclude
dev_langs: C++
helpviewer_keywords: exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f28a4ce5e06687c279d80bc482895c9394726841
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="exclude-import"></a>exclude (#import)
**C + + 专用**  
  
 从要生成的类型库标头文件中排除项。  
  
## <a name="syntax"></a>语法  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
#### <a name="parameters"></a>参数  
 `Name1`  
 要排除的第一项。  
  
 `Name2`  
 要排除的第二项（如果需要）。  
  
## <a name="remarks"></a>备注  
 类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 此特性可以采用任意数量的自变量，每个自变量都是要排除的顶级类型库项。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>另请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)