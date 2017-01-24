---
title: "unchecked_array_iterator 类 | Microsoft Docs"
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
  - "unchecked_array_iterator"
  - "stdext::unchecked_array_iterator"
dev_langs: 
  - "C++"
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unchecked_array_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过 `unchecked_array_iterator` 类，可以将数组或指针包装到未经检查的迭代器。  使用此类作为原始指针或数组的包装器（使用 [make\_unchecked\_array\_iterator](../Topic/make_unchecked_array_iterator.md) 函数）可以有针对性地管理未经检查的指针警告，无需从全局静默处理这些警告。  如果可能，请优先使用此类的经检查版本 [checked\_array\_iterator](../standard-library/checked-array-iterator-class.md)。  
  
> [!NOTE]
>  此类为标准 C\+\+ 库的 Microsoft 扩展。  使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C\+\+ 标准生成环境中。  
  
## 语法  
  
```  
template <class Iterator>  
    class unchecked_array_iterator;  
```  
  
## 备注  
 此类在 [stdext](../standard-library/stdext-namespace.md) 命名空间中定义。  
  
 此为 [checked\_array\_iterator 类](../standard-library/checked-array-iterator-class.md)的未经检查版本，支持所有相同重载和成员。  有关经检查迭代器的功能的更多信息和代码示例，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。  
  
## 要求  
 **标头：**\<iterator\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<iterator\>](../standard-library/iterator.md)   
 [标准模板库](../misc/standard-template-library.md)