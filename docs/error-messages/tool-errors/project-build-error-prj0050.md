---
title: "项目生成错误 PRJ0050 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0050"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0050"
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0050
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未能注册输出。请确保您具有修改注册表的适当权限。  
  
 Visual C\+\+ 生成系统未能注册生成（dll 或 .exe）的输出。  您需要以管理员身份登录才能修改注册表。  
  
 如果生成的是 .dll，可以尝试使用 regsvr32.exe 手动注册 .dll，这样就应显示有关生成失败的原因的信息。  
  
 如果生成的不是 .dll，请查看生成日志以找到引起错误的命令。