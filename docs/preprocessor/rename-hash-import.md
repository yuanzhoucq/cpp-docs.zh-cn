---
title: "重命名 (#import) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Rename
dev_langs:
- C++
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6391f3d88a081da6e01b115389b1a9b986ae6c0f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="rename-import"></a>重命名 (#import)
**C + + 专用**  
  
 解决名称冲突问题。  
  
## <a name="syntax"></a>语法  
  
```  
rename("OldName","NewName")  
```  
  
#### <a name="parameters"></a>参数  
 `OldName`  
 类型库中的旧名称。  
  
 `NewName`  
 要替代旧名称使用的名称。  
  
## <a name="remarks"></a>备注  
 如果指定此特性，编译器将替换出现的所有*OldName*中具有的用户提供的类型库*NewName*生成的标头文件中。  
  
 当类型库中的名称与系统标头文件中的宏定义一致时，可以使用此特性。 如果这种情况下未得到解决，则会生成各种语法错误，如[编译器错误 C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md)和[编译器错误 C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md)。  
  
> [!NOTE]
>  该替换是针对类型库中使用的名称，而不是针对生成的标头文件中的名称。  
  
 例如，假设类型库中存在名为 `MyParent` 的属性，并且在标头文件中定义了宏 `GetMyParent`，在 `#import` 前面使用了该宏。 由于`GetMyParent`是错误处理的包装器函数的默认名称**获取**属性，将发生名称冲突。 若要解决此问题，请在 `#import` 语句中使用以下特性：  
  
```  
rename("MyParent","MyParentX")  
```  
  
 该语句对类型库中的名称 `MyParent` 重命名。 尝试对 `GetMyParent` 包装器名称重命名将失败：  
  
```  
rename("GetMyParent","GetMyParentX")  
```  
  
 这是因为名称 `GetMyParent` 仅在生成的类型库标头文件中出现。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)