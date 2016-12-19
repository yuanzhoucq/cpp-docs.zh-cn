---
title: "删除 CObject 集合中的所有对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject 类集合"
  - "CObject 类, 在集合中删除"
  - "集合类, 删除所有对象"
  - "集合类, 共享对象"
  - "对象 [C++], 在集合中删除"
  - "CObject 集合中的对象"
  - "CObject 集合中的对象, 删除"
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 删除 CObject 集合中的所有对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明如何删除集合中的所有对象 \(不删除集合对象\)。  
  
 若要删除 `CObject`的集合的任何对象 \(从 `CObject`派生的或对象\)，可以使用文中描述的一个迭代技术 [访问集合的所有成员。](../mfc/accessing-all-members-of-a-collection.md) 依次删除每个对象。  
  
> [!CAUTION]
>  集合中的对象可以共享。  也就是说集合保留一个指向对象，但是，程序的其他任何部分还可以指向同一对象。  您必须小心不删除对象，使用共享的对象，直到所有部件完成。  
  
 本文演示如何删除对象中：  
  
-   [一个列表](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)  
  
-   [数组。](#_core_to_delete_all_elements_in_an_array)  
  
-   [映射](#_core_to_delete_all_elements_in_a_map)  
  
#### 删除指针的所有对象。CObject 列表  
  
1.  使用 `GetHeadPosition` 和 `GetNext` 循环访问该列表。  
  
2.  使用 **删除** 运算符来删除每个对象，它在一个迭代时。  
  
3.  否则，在对象与这些元素被删除后，请调用 `RemoveAll` 函数从列表中移除任何元素。  
  
 下面的示例演示如何删除从 `CPerson` 对象列表的任何对象。  列表中的每个对象都是指针对最初堆中分配的 `CPerson` 对象。  
  
 [!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/CPP/deleting-all-objects-in-a-cobject-collection_1.cpp)]  
  
 最后，调用 `RemoveAll`函数，这是列表移除所有元素的列表成员函数。  成员函数 `RemoveAt` 移除一个元素。  
  
 要注意删除元素对象和移除元素之间的区别。  移除元素从列表仅移除对该对象的引用的列表。  对象保留在内存中。  则删除对象时，它将会停止存在，其内存回收。  因此，移除元素很重要，在元素的对象删除之后，以便该列表不会尝试访问不存在的对象。  
  
#### 删除数组中的所有元素  
  
1.  使用 `GetSize` 和整数直至循环访问数组。  
  
2.  使用 **删除** 运算符来删除每个元素，它在一个迭代时。  
  
3.  在删除后，请调用 `RemoveAll` 函数从数组中移除所有元素。  
  
     删除数组的所有元素代码如下所示：  
  
     [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/CPP/deleting-all-objects-in-a-cobject-collection_2.cpp)]  
  
 使用上面的示例的列表，您可以调用 `RemoveAll` 或 `RemoveAt` 的数组中移除所有元素中移除单个元素。  
  
#### 在删除映射的所有元素  
  
1.  使用 `GetStartPosition` 和 `GetNextAssoc` 循环访问该数组。  
  
2.  使用 **删除** 运算符、键和值每个映射元素的，在遇到迭代。  
  
3.  在删除后，请调用 `RemoveAll` 函数从映射中移除所有元素。  
  
     删除的 `CMap` 集合的任何代码元素如下所示。  在映射的每个元素都具有一个字符串用作键和 `CPerson` 对象 \(从 `CObject`派生\) 作为值。  
  
     [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/CPP/deleting-all-objects-in-a-cobject-collection_3.cpp)]  
  
 可以移除映射在调用 `RemoveAll` 或 `RemoveKey` 的所有元素中移除单个元素具有指定键的。  
  
## 请参阅  
 [访问集合的所有成员](../mfc/accessing-all-members-of-a-collection.md)