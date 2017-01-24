---
title: "编译器错误 C2705 | Microsoft Docs"
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
  - "C2705"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2705"
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2705
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“label”: 非法跳转到“exception handler block”范围中  
  
 执行跳转到 `try`\/`catch`、`__try`\/`__except`、`__try`\/`__finally` 块内的标签。  有关更多信息，请参见[异常处理](../../cpp/exception-handling-in-visual-cpp.md)。  
  
 下面的示例生成 C2705：  
  
```  
// C2705.cpp  
int main() {  
goto trouble;  
   __try {  
      trouble: ;   // C2705  
   }  
   __finally {}  
  
   // try the following line instead  
   // trouble: ;  
}  
```