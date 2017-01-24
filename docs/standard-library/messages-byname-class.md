---
title: "messages_byname 类 | Microsoft Docs"
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
  - "messages_byname"
  - "std::messages_byname"
  - "std.messages_byname"
  - "xlocmes/std::messages_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "messages_byname 类"
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
caps.latest.revision: 22
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# messages_byname 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

派生的模板类描述可以充当特定区域设置的信息方面的对象，启用本地化的消息。  
  
## 语法  
  
```  
template<class CharType>  
    class messages_byname : public messages<CharType> {  
public:  
    explicit messages_byname(  
        const char *_Locname,  
        size_t _Refs = 0  
    );  
    explicit messages_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );   
protected:  
    virtual ~messages_byname();  
};  
```  
  
#### 参数  
 `_Locname`  
 命名区域设置。  
  
 `_Refs`  
 初始引用计数。  
  
## 备注  
 命名区域设置行为取决于它的 `_Locname`。  各个构造函数初始化其与 [消息](../Topic/messages::messages.md)\<CharType\>\(`_Refs`\) 的基对象。  
  
## 要求  
 **页眉：** \<区域设置\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)