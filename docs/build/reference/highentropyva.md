---
title: "/HIGHENTROPYVA | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/HIGHENTROPYVA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/HIGHENTROPYVA editbin 选项"
  - "HIGHENTROPYVA editbin 选项"
  - "-HIGHENTROPYVA editbin 选项"
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /HIGHENTROPYVA
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定可执行映像是否支持高熵 64 位地址空间布局随机化 \(ASLR\)。  
  
```  
  
/HIGHENTROPYVA[:NO]  
  
```  
  
## 备注  
 此选项修改 .dll 文件或 .exe 文件的标头，以指示是否支持 64 位地址的 ASLR。  当在可执行文件和所有依赖的模块上执行此选项时，支持 64 位 ASLR 的操作系统可在加载时通过使用 64 位虚拟地址空间来重新设定可执行图像段。  更大的地址空间使攻击者更难猜到特定内存区域的位置。  
  
 默认情况下，链接器为 64 位可执行映像设置此选项。  要设置此选项，还必须设置 [\/DYNAMICBASE](../../build/reference/dynamicbase.md) 选项。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)   
 [\/DYNAMICBASE](../../build/reference/dynamicbase.md)   
 [Windows ISV 软件安全防御措施](http://msdn.microsoft.com/library/bb430720.aspx)