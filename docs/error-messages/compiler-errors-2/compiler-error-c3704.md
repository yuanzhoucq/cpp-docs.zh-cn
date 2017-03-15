---
title: "编译器错误 C3704 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3704"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3704"
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3704
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”：vararg 方法无法激发事件  
  
 尝试将 [\_\_event](../../cpp/event.md) 用于 vararg 方法。  若要修复此错误，请按下面的代码示例所示，将 `fireEvent(int i, ...)` 调用替换为 `fireEvent(int i)` 调用。  
  
 下面的示例生成 C3704：  
  
```  
// C3704.cpp  
[ event_source(native) ]  
class CEventSrc {  
   public:  
      __event void fireEvent(int i, ...);   // C3704  
      // try the following line instead:  
      // __event void fireEvent(int i);  
};  
  
int main() {  
}  
```