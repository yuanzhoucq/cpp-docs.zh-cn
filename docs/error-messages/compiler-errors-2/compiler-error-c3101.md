---
title: "编译器错误 C3101 | Microsoft Docs"
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
  - "C3101"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3101"
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3101
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

命名特性参数“field”的表达式非法  
  
 当初始化命名特性参数时，值必须是一个编译时常数。  
  
 有关特性的更多信息，请参见 [用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3101。  
  
```  
// C3101.cpp  
// compile with: /clr /c  
ref class AAttribute : System::Attribute {  
public:  
   int Field;  
};  
  
extern int i;  
  
[assembly:A(Field = i)];   // C3101  
[assembly:A(Field = 0)];   // OK  
```