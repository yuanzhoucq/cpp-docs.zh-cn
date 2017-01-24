---
title: "链接器工具错误 LNK1188 | Microsoft Docs"
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
  - "LNK1188"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1188"
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1188
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

BADFIXUPSECTION:: 无效的链接地址信息目标“symbol”；可能是零长度节  
  
 在 VxD 链接期间，重定位的目标没有节。  使用 LINK386（早期版本）时，OMF GROUP 记录（由 MASM GROUP 指令生成）可能已经用于将零长度节与另一个非零长度节组合。  COFF 格式不支持 GROUP 指令和零长度节。  当 LINK 自动将此类型的 OMF 对象转换为 COFF 时，可能出现该错误。