---
title: 依赖项副作用 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7537e077a43318a487163d014b49d52cef66ce19
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367519"
---
# <a name="dependency-side-effects"></a>依赖项副作用
如果使用冒号 （:） 中两个依赖项行中不同的位置，指定目标，如果后行之一显示的命令，NMAKE 将解释依赖项，如同相邻或组合。 它不会调用不具有任何命令，而是假定的依赖关系属于一个描述块和执行的命令与其他依赖项指定的依赖关系的推理规则。 例如，这一组规则：  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
```  
  
 计算结果为此：  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 这种效果，则不会使用两个冒号 (`::`) 使用。 例如，这一组规则：  
  
```Output  
bounce.exe :: jump.obj  
   echo Building bounce.exe...  
  
bounce.exe :: up.obj  
```  
  
 计算结果为此：  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
# invokes an inference rule  
```  
  
## <a name="see-also"></a>请参阅  
 [目标](../build/targets.md)