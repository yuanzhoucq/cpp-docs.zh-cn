---
title: "编译器警告（等级 1）C4788 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4788"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4788"
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 1）C4788
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 标识符被截断为“number”个字符  
  
 编译器限制函数名称的最大长度。  编译器为 EH\/SEH 代码生成 funclet 时，通过预置带有某个文本（例如，“\_\_catch”、“\_\_unwind”）或其他字符串的函数名称来形成 funclet 名称。  
  
 得到的 funclet 名称可能太长，编译器会将该名称截断并生成 C4788。  
  
 若要解决此警告，请缩短原始函数名称。  如果函数为 C\+\+ 模板函数或方法，请使用 typedef 作为部分名称。  例如：  
  
```  
C1<x, y, z<T>>::C2<a,b,c>::f  
```  
  
 可被替换为：  
  
```  
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;  
new_class::f  
```  
  
 此警告仅发生在[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]的编译器。