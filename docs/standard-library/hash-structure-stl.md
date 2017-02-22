---
title: "hash 结构 (STL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "thread/std::hash"
dev_langs: 
  - "C++"
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# hash 结构 (STL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义一个成员函数返回一个值，由唯一确定 `Val`。 成员函数定义 [哈希](../standard-library/hash-class.md) 适用于类型的映射值的函数 `thread::id` 索引值的分布。  
  
## <a name="syntax"></a>语法  
  
```  
template <>  
struct hash<thread::id> :   
    public unary_function<thread::id, size_t>  
{  
    size_t operator()(thread::id Val) const;

 
};  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** 线程  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
 [标头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\< 线程>](../standard-library/thread.md)   
 [unary_function 结构](../standard-library/unary-function-struct.md)
