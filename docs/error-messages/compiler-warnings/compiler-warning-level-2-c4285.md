---
title: "编译器警告（等级 2）C4285 | Microsoft Docs"
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
  - "C4285"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4285"
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 2）C4285
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果使用中辍符应用，则“identifier::operator–\> ”的返回类型为递归  
  
 指定的 **operator–\>\(\)** 函数不能返回为其定义的类型或对为其定义的类型的引用。  
  
 下面的示例生成 C4285：  
  
```  
// C4285.cpp  
// compile with: /W2  
class C  
{  
public:  
    C operator->();   // C4285  
   // C& operator->();  C4285, also  
};  
  
int main()  
{  
}  
```