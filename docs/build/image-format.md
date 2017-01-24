---
title: "图像格式 | Microsoft Docs"
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
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 图像格式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可执行的映像格式为 PE32\+。  可执行的映像（DLL 和 EXE）被限制为最大 2 GB，因此可将通过 32 位置换的相对地址用于访问静态映像数据。  此数据包括导入地址表、字符串常数、静态全局数据，等等。  
  
## 请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)