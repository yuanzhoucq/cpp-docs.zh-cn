---
title: "右移 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 右移
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

带符号的整型负值右移位的结果  
  
 将负值向右移位可生成绝对值的一半（向下舍入）。  例如，已签名的 `short` 值 –253（十六进制 0xFF03，二进制 11111111 00000011 ）向右移一位会生成 –127（十六进制 0xFF81，二进制 11111111 10000001）。  正 253 向右移位生成 \+126。  
  
 右移保留带符号的整数类型的符号位。  当带符号的整数向右移位时，最高有效位将保留。  例如，如果 0xF0000000 是带符号的 `int`，则右移位生成 0xF8000000。  将负数 `int` 右移位 32 次会生成 0xFFFFFFFF。  
  
 当无符号的整数右移位时，将清除最高有效位。  例如，如果 0xF000 是无符号的，则结果为 0x7800。  将 `unsigned` 或正数 `int` 右移位 32 次会生成 0x00000000。  
  
## 请参阅  
 [整数](../c-language/integers.md)