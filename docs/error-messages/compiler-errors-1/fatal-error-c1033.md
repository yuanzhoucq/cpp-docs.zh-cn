---
title: "错误 C1033 | Microsoft Docs"
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
  - "C1033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1033"
ms.assetid: 09976c03-8450-4cf7-8b43-1b91c2c2b9f9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法打开程序数据库 pdb  
  
 此错误可能是由磁盘错误导致的。  
  
 在 Visual C\+\+ .NET 2002 中，当文件名（或文件名的目录路径）包含 MBCS 字符时，必须正确设置用户区域设置。  设置系统区域设置是不够的；必须设置用户区域设置才能处理 MBCS 字符。  
  
 有关详细信息,请参阅 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;246007](http://support.microsoft.com/default.aspx?scid=kb;en-us;246007)。