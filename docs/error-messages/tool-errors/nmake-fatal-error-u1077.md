---
title: "NMAKE 错误 U1077 | Microsoft Docs"
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
  - "U1077"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1077"
ms.assetid: 70d989f8-ef34-4ad7-8fe0-5b800556b2a1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 错误 U1077
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“program”: 返回代码“value”  
  
 NMAKE 所调用的给定命令或程序失败并返回给定的退出代码。  
  
 若要取消该错误并继续 NMAKE 会话，请使用 \/I 选项、**.IGNORE** 点指令或短划线 \(**\-**\) 命令修饰符。  若要继续依赖项树不相关部分的 NMAKE 会话，请使用 \/K 选项。