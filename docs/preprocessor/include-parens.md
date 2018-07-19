---
title: include （) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- include()
dev_langs:
- C++
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 756aea4400d98b2bf061a54955b3df4b4eddd993
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849270"
---
# <a name="include"></a>include()
**C + + 专用**  
  
 禁用自动排除。  
  
## <a name="syntax"></a>语法  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### <a name="parameters"></a>参数  
 `Name1`  
 要强制包含的第一项。  
  
 `Name2`  
 要强行包含的第二项（如果需要）。  
  
## <a name="remarks"></a>备注  
 类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 `#import` 尝试通过自动排除此类项来避免多个定义错误。 如果已排除项，如所示[编译器警告 （等级 3） C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)，并且也不应已，可以使用此属性来禁用自动排除。 此特性可采用任意数量的自变量，每个自变量都是要包含的类型库项的名称。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)