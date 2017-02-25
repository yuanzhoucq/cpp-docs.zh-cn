---
title: "/APPCONTAINER | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/APPCONTAINER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/APPCONTAINER editbin 选项"
  - "APPCONTAINER editbin 选项"
  - "-APPCONTAINER editbin 选项"
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /APPCONTAINER
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标记必须在应用容器中运行的可执行文件 \- 例如，[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 或通用 Windows 应用。  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## 备注  
 设置了 **\/APPCONTAINER** 选项的可执行文件只能在应用容器中运行，应用容器是 Windows 8 中引入的进程隔离环境。 对于 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 和通用 Windows 应用，必须设置此选项。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)   
 [什么是通用 Windows 应用？](http://go.microsoft.com/fwlink/p/?LinkID=522074)