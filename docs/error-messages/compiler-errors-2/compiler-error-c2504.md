---
title: "编译器错误 C2504 | Microsoft Docs"
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
  - "C2504"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2504"
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2504
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 未定义基类  
  
 声明了基类但一直没有定义它。可能的原因：  
  
1.  缺少包含文件。  
  
2.  没有用 [extern](../../cpp/using-extern-to-specify-linkage.md) 声明外部基类。  
  
 下面的示例生成 C2504：  
  
```  
// C2504.cpp  
// compile with: /c  
class A;  
class B : public A {};   // C2504  
```  
  
 \/\/ OK  
  
```  
class C{};  
class D : public C {};  
```