---
title: "编译器错误 C2833 | Microsoft Docs"
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
  - "C2833"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2833"
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2833
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator operator”不是可识别的运算符或类型  
  
 单词 `operator` 后面必须跟有要重写的运算符或要转换的类型。  
  
 要获得可在托管类型中定义的运算符的列表，请参见[用户定义的运算符](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
 下面的示例生成 C2833：  
  
```  
// C2833.cpp  
// compile with: /c  
class A {};  
  
void operator ::* ();   // C2833  
void operator :: ();   // OK  
```