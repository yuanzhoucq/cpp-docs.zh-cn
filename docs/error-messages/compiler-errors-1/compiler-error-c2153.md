---
title: "编译器错误 C2153 | Microsoft Docs"
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
  - "C2153"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2153"
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2153
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

十六进制常数必须至少有一个十六进制数字  
  
 十六进制常数 0x、0X 和 \\x 无效。  至少有一个十六进制数字必须跟在 x 或 X 之后。  
  
 下面的示例生成 C2153：  
  
```  
// C2153.cpp  
int main() {  
   int a= 0x;    // C2153  
   int b= 0xA;   // OK  
}  
```