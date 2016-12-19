---
title: "编译器错误 C3170 | Microsoft Docs"
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
  - "C3170"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3170"
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3170
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在一个项目中不能有不同的模块标识符  
  
 在一次编译中的两个文件内发现了名称不同的 [module](../../windows/module-cpp.md) 特性。  每次编译只能指定一个唯一的 `module` 特性。  
  
 可在一个以上的源代码文件中指定相同的 `module` 特性。  
  
 例如，如果发现了以下 module 特性：  
  
```  
// C3170.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
int main() {}  
```  
  
 然后，  
  
```  
// C3170b.cpp  
// compile with: C3170.cpp  
// C3170 expected  
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
```  
  
 编译器将生成 C3170（请记下不同的名称）。