---
title: "编译器错误 C3896 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3896"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3896"
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3896
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”: 不正确的初始值设定项: 此 literal 数据成员只能使用“nullptr”进行初始化  
  
 [文本](../../windows/literal-cpp-component-extensions.md) 数据成员未正确初始化。有关更多信息，请参见[nullptr](../../windows/nullptr-cpp-component-extensions.md)。  
  
 下面的示例生成 C3896：  
  
```  
// C3896.cpp  
// compile with: /clr /c  
ref class R{};  
  
value class V {  
   literal R ^ r = "test";   // C3896  
   literal R ^ r2 = nullptr;   // OK  
};  
```