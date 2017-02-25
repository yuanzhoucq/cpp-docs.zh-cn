---
title: "链接器工具错误 LNK1241 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1241"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1241"
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具错误 LNK1241
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已指定资源文件“resource file”  
  
 如果从命令行手动运行 **cvtres**，然后将得到的 .obj 文件和其他 .res 文件一起传递给链接器，则会生成此错误。  
  
 若要指定多个 .res 文件，请将它们全部作为 .res 文件传递给链接器，而不要从 **cvtres** 创建的 .obj 文件内传递。