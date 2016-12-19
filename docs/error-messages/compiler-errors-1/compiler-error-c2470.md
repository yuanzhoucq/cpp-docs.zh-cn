---
title: "编译器错误 C2470 | Microsoft Docs"
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
  - "C2470"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2470"
ms.assetid: e17d2cb8-b84c-447c-976a-625f0c96f3fe
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2470
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 看起来像函数定义，但没有参数列表；跳过明显的函数体  
  
 函数定义缺少其参数列表。  
  
 下面的示例生成 C2470：  
  
```  
// C2470.cpp  
int MyFunc {};  // C2470  
void MyFunc2() {};  //OK  
  
int main(){  
   MyFunc();  
   MyFunc2();  
}  
```