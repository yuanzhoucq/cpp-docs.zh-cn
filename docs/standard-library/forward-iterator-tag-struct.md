---
title: "forward_iterator_tag 结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xutility/std::forward_iterator_tag
dev_langs: C++
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4874163e1060658c03757507cba2953c35c56557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag 结构
一种为代表向前迭代器的 **iterator_category** 函数提供返回类型的类。  
  
## <a name="syntax"></a>语法  
  
```
struct forward_iterator_tag    : public input_iterator_tag {};
```  
  
## <a name="remarks"></a>备注  
 分类标记类用作算法选择的编译标记。 模板函数需要查找其迭代器参数的最具体的分类，以便可以在编译时使用最高效的算法。 对于每个 `Iterator` 类型的迭代器，`iterator_traits`< `Iterator`> **::iterator_category** 必须定义为最具体的分类标记，用于描述迭代器的行为。  
  
 当 **Iter** 描述一个可充当正向迭代器的对象时，其类型与 **iterator**\< **Iter**> **::iterator_category** 相同。  
  
## <a name="example"></a>示例  
 有关如何使用 **iterator_tag** 的示例，请参阅 [iterator_traits](../standard-library/iterator-traits-struct.md) 或 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<iterator>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [input_iterator_tag 结构](../standard-library/input-iterator-tag-struct.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)



