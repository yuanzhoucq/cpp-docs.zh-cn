---
title: "/INTEGRITYCHECK | Microsoft Docs"
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
  - "/INTEGRITYCHECK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/INTEGRITYCHECK editbin 选项"
  - "INTEGRITYCHECK editbin 选项"
  - "-INTEGRITYCHECK editbin 选项"
ms.assetid: 2a293705-4396-421b-a5a5-693b4b867a85
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /INTEGRITYCHECK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定二进制图像的数字签名在加载时必须进行检查。  
  
```  
  
/INTEGRITYCHECK[:NO]  
  
```  
  
## 备注  
 在 DLL 文件或可执行文件的标头中，此选项可设置标志，以设置要求内存管理器先检查数字签名然后再在 Windows 中加载图像。  Windows Vista 之前的各个 Windows 版本忽略此标志。  建议在所有的设备驱动程序中，必须为实现核心架构代码的 64 位 DLL 设置此选项。  有关详细信息，请参见 MSDN 网站上的 [Kernel\-Mode Code Signing Walkthrough](http://go.microsoft.com/fwlink/?linkid=237093)（内核模式代码签名演练）。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)