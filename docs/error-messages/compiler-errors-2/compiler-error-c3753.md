---
title: "编译器错误 C3753 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3753"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3753"
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器错误 C3753
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允许使用泛型属性  
  
 泛型参数列表只能出现在托管类、结构、或函数上。  
  
 有关更多信息，请参见[泛型](../../windows/generics-cpp-component-extensions.md)和[属性](../../windows/property-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3753。  
  
```  
// C3753.cpp  
// compile with: /clr /c  
ref struct A {  
   generic <typename T>  
   property int i;   // C3753 error  
};  
```