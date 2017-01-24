---
title: "type_index 类 | Microsoft Docs"
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
  - "typeindex/std::type_index"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "type_index 类"
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
caps.latest.revision: 14
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# type_index 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`type_index` 类包装指向 [type\_info 类](../cpp/type-info-class.md) 帮助索引由这样的对象。  
  
```  
class type_index {  
public:  
    type_index(const type_info& tinfo);  
    const char *name() const;  
    size_t hash_code() const;  
    bool operator==(const type_info& right) const;  
    bool operator!=(const type_info& right) const;  
    bool operator<(const type_info& right) const;  
    bool operator<=(const type_info& right) const;  
    bool operator>(const type_info& right) const;  
    bool operator>=(const type_info& right) const;  
};  
```  
  
 构造函数初始化 `ptr` 设置为 `&tinfo`。  
  
 `name` 返回 `ptr->name()`。  
  
 `hash_code` 返回了 `ptr->hash_code().`  
  
 `operator==` 返回 `*ptr == right.ptr`。  
  
 `operator!=` 返回 `!(*this == right)`。  
  
 `operator<` 返回 `*ptr->before(*right.ptr)`。  
  
 `operator<=` 返回了 `!(right < *this).`  
  
 `operator>`的返回 `right < *this`。  
  
 `operator>=` 返回 `!(*this < right)`。  
  
## 请参阅  
 [运行时类型信息](../cpp/run-time-type-information.md)   
 [\<typeindex\>](../standard-library/typeindex.md)