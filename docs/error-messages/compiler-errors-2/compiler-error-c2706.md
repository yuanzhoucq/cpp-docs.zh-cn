---
title: "编译器错误 C2706 | Microsoft Docs"
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
  - "C2706"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2706"
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2706
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

没有匹配 \_\_try 的非法 \_\_except\(\_\_try 块中是否缺少“}”？\)  
  
 编译器没有找到 `__try` 块的右大括号。  
  
 下面的示例生成 C2706：  
  
```  
// C2706.cpp  
int main() {  
   __try {  
      void f();  
   // C2706  } missing here  
   __except(GetExceptionCode() == 0x0) {  
   }  
}  
```