---
title: "allocator&lt;void&gt; 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
dev_langs:
- C++
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: d816804e15e7a02edbe07f131529bf719039459f
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt; 类
一种针对 `void` 类型进行的模板类分配器专用化，用于定义在此上下文中有意义的类型。  
  
## <a name="syntax"></a>语法  
  
```
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```  
  
## <a name="remarks"></a>备注  
 类为类型 *void 显式指定模板类 [allocator](../standard-library/allocator-class.md)。* 其构造函数和赋值运算符与模板类的行为方式相同，但它仅定义以下类型：  
  
- [const_pointer](../standard-library/allocator-class.md#const_pointer)。  
  
- [pointer](../standard-library/allocator-class.md#pointer)。  
  
- [value_type](../standard-library/allocator-class.md#value_type)。  
  
- [rebind](../standard-library/allocator-class.md#rebind), a nested template class.  
  
## <a name="requirements"></a>要求  
 **标头：**\<memory>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




