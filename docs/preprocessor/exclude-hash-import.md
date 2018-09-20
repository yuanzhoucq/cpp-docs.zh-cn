---
title: 排除 (#import) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- exclude
dev_langs:
- C++
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5798c7515c411b9abf9d10229a6185e01bb92f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400193"
---
# <a name="exclude-import"></a>exclude (#import)
**C + + 专用**  
  
从要生成的类型库标头文件中排除项。  
  
## <a name="syntax"></a>语法  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
### <a name="parameters"></a>参数  
*Name1*  
要排除的第一项。  
  
*Name2*  
要排除的第二项（如果需要）。  
  
## <a name="remarks"></a>备注  
 
类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 此特性可以采用任意数量的自变量，每个自变量都是要排除的顶级类型库项。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)