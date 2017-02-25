---
title: "编译器错误 C2492 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2492"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2492"
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2492
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“variable”:“thread”数据可能没有 dll 接口  
  
 使用 [thread](../../cpp/thread.md) 特性和 DLL 接口声明了该变量。  `thread` 变量的地址直到运行时才已知，所以无法将它链接到 DLL 导入或导出。  
  
 下面的示例生成 C2492：  
  
```  
// C2492.cpp  
// compile with: /c  
class C {  
public:  
   char   ch;  
};  
  
__declspec(dllexport) __declspec(thread) C c_1;   // C2492  
__declspec(thread) C c_1;   // OK  
```