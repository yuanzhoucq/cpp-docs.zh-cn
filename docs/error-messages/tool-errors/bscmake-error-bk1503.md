---
title: "BSCMAKE 错误 BK1503 | Microsoft Docs"
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
  - "BK1503"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1503"
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 错误 BK1503
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法写入文件“文件名”\[: 原因\]  
  
 BSCMAKE 将编译期间生成的 .sbr 文件组合到一个浏览器数据库中。  如果结果浏览器数据库超过 64 MB，或者如果输入文件 \(.sbr\) 数超过 4092 个，则将引发该错误。  
  
 如果此问题是由 .sbr 文件数多于 4092 个造成的，则必须减小输入文件的数目。  在 Visual Studio 中，这可以通过 [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) 整个项目，然后逐一再次检查文件来完成。  
  
 如果此问题是由 .bsc 文件大于 64MB 造成的，则减少作为输入的 .sbr 文件数将减小结果 .bsc 文件的大小。  此外，浏览信息量也可通过使用 \/Em（排除宏扩展符号）、\/El（排除局部变量）和 \/Es（排除系统文件）来减少。  
  
## 请参阅  
 [BSCMAKE 选项](../../build/reference/bscmake-options.md)