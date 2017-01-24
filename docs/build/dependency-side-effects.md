---
title: "依赖项副作用 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "依赖项副作用"
  - "NMAKE 程序，依赖项"
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 依赖项副作用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果用冒号 （:） 位于不同位置的两个相关行中指定目标，并且命令会显示在命令行之一后，NMAKE 将解释这些依赖项，如同相邻或组合。 它不会调用没有命令，而是假定的依赖关系隶属于一个描述块和执行其他依赖于指定的命令的依赖关系的推理规则。 例如，此规则集︰  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
```  
  
 计算如下︰  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 这种效果，则不会使用两个冒号 (`::`) 使用。 例如，此规则集︰  
  
```Output  
bounce.exe :: jump.obj  
   echo Building bounce.exe...  
  
bounce.exe :: up.obj  
```  
  
 计算如下︰  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
# invokes an inference rule  
```  
  
## <a name="see-also"></a>另请参阅  
 [目标](../build/targets.md)