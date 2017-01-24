---
title: "多个目标 | Microsoft Docs"
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
  - "生成文件目标"
  - "NMAKE 中的多个目标"
  - "多个 NMAKE 中的目标"
  - "NMAKE 程序中目标"
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 多个目标
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE 评估单个依赖项中的多个目标就像每个单独的描述块中指定。  
  
 例如，以下...  
  
```Output  
bounce.exe leap.exe : jump.obj  
   echo Building...  
```  
  
 ...是计算如下︰  
  
```Output  
bounce.exe : jump.obj  
   echo Building...  
leap.exe : jump.obj  
   echo Building...  
```  
  
## <a name="see-also"></a>另请参阅  
 [目标](../build/targets.md)