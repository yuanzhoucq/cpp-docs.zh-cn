---
title: 如何： 创建和使用 unique_ptr 实例 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae4610e7b26eecd6ef444f3c7c73e95af365ca71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-and-use-uniqueptr-instances"></a>如何：创建和使用 unique_ptr 实例
A [unique_ptr](../standard-library/unique-ptr-class.md)不共享它的指针。 无法将复制到另一个`unique_ptr`、 按值传递给函数，或需要副本进行任何 C++ 标准库算法中使用。 只能移动 `unique_ptr`。 这意味着，内存资源所有权将转移到另一 `unique_ptr`，并且原始 `unique_ptr` 不再拥有此资源。 我们建议你将对象限制为由一个所有者所有，因为多个所有权会使程序逻辑变得复杂。 因此，您需要为普通的 C++ 对象的智能指针，则使用`unique_ptr`，而当构造`unique_ptr`，使用[make_unique](../standard-library/memory-functions.md#make_unique)帮助器函数。  
  
 下图演示了两个 `unique_ptr` 实例之间的所有权转换。  
  
 ![移动的唯一 & #95; 所有权 ptr](../cpp/media/unique_ptr.png "unique_ptr")  
  
 `unique_ptr`在中定义`<memory>`C++ 标准库中的标头。 这正是与原始指针有效并可在 C++ 标准库容器。 添加`unique_ptr`到 C++ 标准库容器的实例是高效因为移动构造函数的`unique_ptr`无需进行复制操作。  
  
## <a name="example"></a>示例  
 以下示例演示如何创建 `unique_ptr` 实例并在函数之间传递这些实例。  
  
 [!code-cpp[stl_smart_pointers#210](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]  
  
 这些示例说明了 `unique_ptr` 的基本特征：可移动，但不可复制。 “移动”将所有权转移到新 `unique_ptr` 并重置旧 `unique_ptr`。  
  
## <a name="example"></a>示例  
 以下示例演示如何创建 `unique_ptr` 实例并在向量中使用这些实例。  
  
 [!code-cpp[stl_smart_pointers#211](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]  
  
 在 range for 循环中，注意 `unique_ptr` 通过引用来传递。 如果你尝试通过此处的值传递，由于删除了 `unique_ptr` 复制构造函数，编译器将引发错误。  
  
## <a name="example"></a>示例  
 以下示例演示如何初始化类成员 `unique_ptr`。  
  
 [!code-cpp[stl_smart_pointers#212](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]  
  
## <a name="example"></a>示例  
 你可以使用[make_unique](../standard-library/memory-functions.md#make_unique)创建`unique_ptr`到一个数组，但不是能使用`make_unique`初始化数组元素。  
  
 [!code-cpp[stl_smart_pointers#213](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]  
  
 有关更多示例，请参阅[make_unique](../standard-library/memory-functions.md#make_unique)。  
  
## <a name="see-also"></a>请参阅  
 [智能指针](../cpp/smart-pointers-modern-cpp.md)   
 [make_unique](../standard-library/memory-functions.md#make_unique)