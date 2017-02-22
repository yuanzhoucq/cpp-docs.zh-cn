---
title: "链接器工具警告 LNK4086 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4086"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4086"
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 链接器工具警告 LNK4086
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

入口点“function”不是带有“number”字节参数的 \_\_stdcall；映像可能不能运行  
  
 DLL 的入口点必须是 `__stdcall`。  用 [\/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) 选项重新编译该函数，或在定义该函数时指定 `__stdcall` 或 WINAPI。