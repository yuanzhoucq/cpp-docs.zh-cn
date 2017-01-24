---
title: "编译器警告（等级 4）C4324 | Microsoft Docs"
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
  - "C4324"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4324"
ms.assetid: 420fa929-d9c0-40b4-8808-2d8ad3ca8090
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4324
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“struct\_name”: 由于 \_\_declspec\(align\(\)\)，结构被填充  
  
 由于您指定了 [\_\_declspec\(align\)](../../cpp/align-cpp.md) 值，因此是在结构结尾添加的填充。  
  
 例如，以下代码生成 C4324：  
  
```  
// C4324.cpp  
// compile with: /W4  
struct __declspec(align(32)) A  
{  
   char a;  
};   // C4324  
  
int main()  
{  
}  
```