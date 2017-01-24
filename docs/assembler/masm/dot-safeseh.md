---
title: ".SAFESEH | Microsoft Docs"
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
  - ".SAFESEH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "registering functions as exception handlers"
  - "SAFESEH directive"
  - ".SAFESEH directive"
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SAFESEH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

注册作为结构化异常处理程序。  
  
## 语法  
  
```  
  
.SAFESEH identifier  
```  
  
## 备注  
 *标识符* 必须是本地定义的 [PROC](../../assembler/masm/proc.md) 或 [EXTRN](../../assembler/masm/extrn.md) 的 PROC ID。  [标签](../../assembler/masm/label-masm.md) 不允许的。  .SAFESEH 指令要求 [\/safeseh](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe 命令行选项。  
  
 有关结构化异常处理程序的更多信息，请参见 [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)。  
  
 例如，若要注册一个安全异常处理程序，请创建一个新的 MASM 文件 \(如下\)，聚合与 \/safeseh，并将其添加到链接对象。  
  
```  
.386  
.model  flat  
MyHandler   proto  
.safeseh    MyHandler  
end  
```  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)