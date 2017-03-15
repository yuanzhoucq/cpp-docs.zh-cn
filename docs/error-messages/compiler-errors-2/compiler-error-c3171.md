---
title: "编译器错误 C3171 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3171"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3171"
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3171
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“module”: 在一个项目中不能指定不同的模块特性  
  
 在一次编译中的两个文件内发现了具有不同参数列表的 [module](../../windows/module-cpp.md) 特性。  每次编译只能指定一个唯一的 `module` 特性。  
  
 可在一个以上的源代码文件中指定相同的 `module` 特性。  
  
 例如，如果找到以下 `module` 特性：  
  
```  
// C3171.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];  
int main() {}  
```  
  
 然后，  
  
```  
// C3171b.cpp  
// compile with: C3171.cpp  
// C3171 expected  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];  
```  
  
 编译器将生成 C3171（注意不同的版本值）。