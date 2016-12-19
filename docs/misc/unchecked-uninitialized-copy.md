---
title: "unchecked_uninitialized_copy | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_uninitialized_copy"
  - "unchecked_uninitialized_copy"
  - "std::unchecked_uninitialized_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_uninitialized_copy 函数"
ms.assetid: 38568841-314e-446b-91d0-92cc231e3b3c
caps.latest.revision: 9
caps.handback.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_uninitialized_copy
与 [uninitialized\_copy](../Topic/uninitialized_copy.md) 相同，但在定义 \_SECURE\_SCL\=1 时，允许使用未检查的迭代器作为输出迭代器。 在定义了此功能 [stdext 命名空间](../standard-library/stdext-namespace.md) 命名空间。  
  
> [!NOTE]
>  此算法是标准 C\+\+ 库的 Microsoft 扩展。 使用此算法实现的代码将不可移植。  
  
## 语法  
  
```  
template<class InputIterator, class ForwardIterator>  
   ForwardIterator unchecked_uninitialized_copy(  
      InputIterator _First,  
      InputIterator _Last,  
      ForwardIterator _Dest  
   );  
  
template<class InputIterator, class ForwardIterator, class Allocator>  
   ForwardIterator unchecked_uninitialized_copy(  
      InputIterator _First,  
      InputIterator _Last,  
      ForwardIterator _Dest,  
      Allocator& _Al  
   );  
```  
  
#### 参数  
 `_First`  
 在要复制的源范围中发现第一个元素的输入迭代器。  
  
 `_Last`  
 在要复制的源范围中发现最后一个元素的输入迭代器。  
  
 `_Dest`  
 在要复制的目标范围中发现第一个元素的向前迭代器。  
  
 `_Al`  
 要用于此对象的分配器类。[vector::get\_allocator](../Topic/vector::get_allocator.md) 返回该对象的分配器类。  
  
## 返回值  
 向前迭代器，此迭代器在收到副本的目标范围内发现最后一个元素之后的位置。  
  
## 备注  
 请参阅 [uninitialized\_copy](../Topic/uninitialized_copy.md) 有关代码示例。  
  
 检查迭代器的详细信息，请参阅 [经过检查的迭代器](../standard-library/checked-iterators.md)。  
  
## 要求  
 **标头：**\<memory\>  
  
 **命名空间：**stdext