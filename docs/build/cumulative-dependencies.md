---
title: "累计依赖项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "依赖项累计"
  - "NMAKE 中的累计依赖项"
  - "依赖项"
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 累计依赖项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果重复目标依赖关系是累积在描述块中。  
  
 例如，此规则集，  
  
```Output  
bounce.exe : jump.obj  
bounce.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 计算如下︰  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 在单个描述块中的多个相关行中的多个目标就像在单独的描述块中，指定了每个但不是最后一个依赖项行中的目标并不使用命令块计算。 NMAKE 尝试为这些目标使用一条推理规则。  
  
 例如，此规则集，  
  
```Output  
leap.exe bounce.exe : jump.obj  
bounce.exe climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 计算如下︰  
  
```Output  
  
leap.exe : jump.obj  
# invokes an inference rule  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
## <a name="see-also"></a>另请参阅  
 [目标](../build/targets.md)