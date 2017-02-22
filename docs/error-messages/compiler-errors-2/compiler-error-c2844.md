---
title: "编译器错误 C2844 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2844"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2844"
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2844
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”: 不能是接口“interface”的成员  
  
 [接口类](../../windows/interface-class-cpp-component-extensions.md) 无法包含数据成员，除非它也是一个属性。  
  
 接口中不允许除属性或成员函数以外的任何内容。  此外，也不允许构造函数、析构函数和运算符。  
  
 下面的示例生成 C2844：  
  
```  
// C2844a.cpp  
// compile with: /clr /c  
public interface class IFace {  
   int i;   // C2844  
   // try the following line instead  
   // property int Size;  
};  
```  
  
 下面的示例生成 C2844：  
  
```  
// C2844b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
__gc __interface IFace {  
   int i;   // C2844  
   // try the following line instead  
   // __property int Size { get; set; };  
};  
```