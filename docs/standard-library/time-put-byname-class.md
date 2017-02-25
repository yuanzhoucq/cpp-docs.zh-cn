---
title: "time_put_byname 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "time_put_byname"
  - "xloctime/std::time_put_byname"
  - "std.time_put_byname"
  - "std::time_put_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_put_byname 类"
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# time_put_byname 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

派生的模板类描述一个对象来充当区域设置 facet，类型的 `time_put`\< CharType、 OutputIterator \>。  
  
## 语法  
  
```  
template<class CharType,  
 class OutIt = ostreambuf_iterator<CharType, char_traits<CharType> > >  
 class time_put_byname : public time_put<CharType, OutputIterator>  
{  
public:  
    explicit time_put_byname(  
        const char *_Locname,  
        size_t _Refs = 0  
    );  
    explicit time_put_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );  
protected:  
    virtual ~time_put_byname();  
};  
```  
  
#### 参数  
 `_Locname`  
 区域设置名称。  
  
 `_Refs`  
 初始引用计数。  
  
## 备注  
 其行为由 [名为](../Topic/locale::name.md) 区域设置 `_Locname`。 每个构造函数初始化与与其基对象 [time\_put](../Topic/time_put::time_put.md)\< CharType、 OutputIterator \> \(`_Refs`\)。  
  
## 要求  
 **标头：**\<locale\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)