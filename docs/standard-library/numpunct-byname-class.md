---
title: "numpunct_byname 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.numpunct_byname"
  - "numpunct_byname"
  - "xlocnum/std::numpunct_byname"
  - "std::numpunct_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numpunct_byname 类"
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# numpunct_byname 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

派生的模板类描述可以充当特定区域设置启用 `numpunct` 个数字和布尔表达式的格式和标点的对象。  
  
## 语法  
  
```  
template<Class CharType>  
    class numpunct_byname : public numpunct<Elem> {  
public:  
    explicit numpunct_byname(  
        const char* _Locname,  
        size_t _Refs = 0  
    );  
    explicit numpunct_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );  
protected:  
    virtual ~numpunct_byname( );  
   };  
```  
  
## 备注  
 [命名的](../Topic/locale::name.md) 区域设置行为取决于它的 `_Locname`。  构造函数初始化其与 [numpunct](../Topic/numpunct::numpunct.md)CharType\<\(\>`_Refs`\) 的基对象。  
  
## 要求  
 **页眉：** \<区域设置\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)