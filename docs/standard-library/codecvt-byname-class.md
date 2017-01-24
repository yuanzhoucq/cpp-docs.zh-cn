---
title: "codecvt_byname 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.codecvt_byname"
  - "codecvt_byname"
  - "std::codecvt_byname"
  - "xlocale/std::codecvt_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt_byname 类"
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
caps.latest.revision: 24
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt_byname 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一对象可以充当特定区域排列的设置方面的派生模板类，使特定信息检索对与转换的文化区域。  
  
## 语法  
  
```  
template<Class CharType, class Byte, class StateType>  
    class codecvt_byname: public codecvt<CharType, Byte, StateType> {  
public:  
    explicit codecvt_byname(  
        const char* _Locname,  
        size_t _Refs = 0  
    );  
```  
  
```  
explicit codecvt_byname(  
    const string& _Locname,  
    size_t _Refs = 0  
);  
```  
  
```  
protected:  
    virtual ~codecvt_byname( );  
};  
```  
  
#### 参数  
 `_Locname`  
 命名区域设置。  
  
 `_Refs`  
 初始引用计数。  
  
## 备注  
 在命名区域设置构造时，Byname 方面自动创建。  
  
 命名区域设置行为取决于它的 `_Locname`。  各个构造函数初始化其与 [codecvt](../standard-library/codecvt-class.md)\<CharType，字节，StateType\>\(`_Refs`\) 的基对象。  
  
## 要求  
 **页眉：** \<区域设置\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)