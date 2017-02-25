---
title: "/DYNAMICBASE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/dynamicbase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DYNAMICBASE editbin 选项"
  - "DYNAMICBASE editbin 选项"
  - "-DYNAMICBASE editbin 选项"
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /DYNAMICBASE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定是否可在加载时使用地址空间布局随机化 \(ASLR\) 功能随机重新设定可执行映像的基址。  
  
## 语法  
  
```  
  
/DYNAMICBASE[:NO]  
```  
  
## 备注  
 默认情况下，链接器设置 **\/DYNAMICBASE** 选项。  
  
 此选项修改可执行映像的标头以指示加载程序是否可以在加载时随机重新设定映像的基址。  
  
 Windows Vista、Windows Server 2008、Windows 7、Windows 8 和 Windows Server 2012 支持 ASLR。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)   
 [Windows ISV 软件安全防御措施](http://msdn.microsoft.com/library/bb430720.aspx)