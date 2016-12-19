---
title: "&lt;memory&gt; | Microsoft Docs"
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
  - "memory/std::<memory>"
  - "std.<memory>"
  - "<memory>"
  - "std::<memory>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "memory 标头"
ms.assetid: ef8e38da-7c9d-4037-9ad1-20c99febf5dc
caps.latest.revision: 22
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;memory&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义一个类、运算符和一些模板来帮助分配和释放对象。  
  
## 语法  
  
```  
  
#include <memory>  
  
```  
  
## 成员  
  
### Functions  
  
|||  
|-|-|  
|[addressof](../Topic/addressof.md)|获取对象的实际地址。|  
|[align](../Topic/align.md)|根据所提供的对齐和起始地址，返回指向给定大小范围的指针。|  
|[allocate\_shared](../Topic/allocate_shared.md)|创建一个 `shared_ptr`，指向使用指定分配器分配和构造的给定类型的对象。|  
|[checked\_uninitialized\_copy](../misc/checked-uninitialized-copy.md)|与 `uninitialized_copy` 相同，但强制使用检查迭代器作为输出迭代器。|  
|[checked\_uninitialized\_fill\_n](../misc/checked-uninitialized-fill-n.md)|与 `uninitialized_fill_n` 相同，但强制使用检查迭代器作为输出迭代器。|  
|[const\_pointer\_cast](../Topic/const_pointer_cast.md)|常量强制转换为 `shared_ptr`。|  
|[declare\_no\_pointers](../Topic/declare_no_pointers.md)|通知垃圾回收器：从指定地址开始且属于所指示块大小范围内的字符不包含可跟踪的指针。|  
|[declare\_reachable](../Topic/declare_reachable.md)|通知垃圾回收器：所指示的地址属于分配的存储并可到达。|  
|[default\_delete](../Topic/default_delete.md)|删除使用 `operator new` 分配的对象。  适合与 `unique_ptr` 一起使用。|  
|[dynamic\_pointer\_cast](../Topic/dynamic_pointer_cast.md)|动态强制转换为 `shared_ptr`。|  
|[get\_deleter](../Topic/get_deleter%20Function.md)|从 `shared_ptr` 获取删除器。|  
|[get\_pointer\_safety](../Topic/get_pointer_safety.md)|返回任意垃圾回收器所采用的指针安全类型。|  
|[get\_temporary\_buffer](../Topic/get_temporary_buffer.md)|为不超过指定元素数量的元素序列分配临时存储。|  
|[make\_shared](../Topic/make_shared%20\(%3Cmemory%3E\).md)|创建并返回一个 `shared_ptr`，指向使用默认分配器从零个或多个参数构造的分配对象。|  
|[make\_unique](../Topic/make_unique.md)|创建并返回一个 [unique\_ptr](../standard-library/unique-ptr-class.md)，指向从零个或多个参数构建的分配对象。|  
|[owner\_less](../Topic/owner_less.md)|允许对共享指针和弱指针进行基于所有权的混合比较。|  
|[pointer\_safety](../Topic/pointer_safety%20Enumeration.md)|一种对 `get_pointer_safety` 的所有可能返回值的枚举。|  
|[return\_temporary\_buffer](../Topic/return_temporary_buffer.md)|对使用 `get_temporary_buffer` 模板函数分配的临时内存执行解除分配。|  
|[static\_pointer\_cast](../Topic/static_pointer_cast.md)|静态强制转换为 `shared_ptr`。|  
|[swap](../Topic/swap%20\(C++%20Standard%20Library\).md)|交换两个 `shared_ptr` 或 `weak_ptr` 对象。|  
|[unchecked\_uninitialized\_copy](../misc/unchecked-uninitialized-copy.md)|与 `uninitialized_copy` 相同，但在定义 \_SECURE\_SCL\=1 时，允许使用未检查的迭代器作为输出迭代器。|  
|[unchecked\_uninitialized\_fill\_n](../misc/unchecked-uninitialized-fill-n.md)|与 `uninitialized_fill_n` 相同，但在定义 \_SECURE\_SCL\=1 时，允许使用未检查的迭代器作为输出迭代器。|  
|[undeclare\_no\_pointers](../Topic/undeclare_no_pointers.md)|通知垃圾回收器：通过基地址指针和块大小而定义的内存块中的字符现在可包含可跟踪的指针。|  
|[undeclare\_reachable](../Topic/undeclare_reachable.md)|通知 `garbage_collector`：指定的内存位置无法达到。|  
|[uninitialized\_copy](../Topic/uninitialized_copy.md)|将来自指定输入范围的对象复制到未初始化的目标范围。|  
|[uninitialized\_copy\_n](../Topic/uninitialized_copy_n.md)|创建来自输入迭代器的指定数量的元素的副本。  副本放置在向前迭代器中。|  
|[uninitialized\_fill](../Topic/uninitialized_fill.md)|将具有指定值的对象复制到未初始化的目标范围。|  
|[uninitialized\_fill\_n](../Topic/uninitialized_fill_n.md)|将具有指定值的对象复制到未初始化目标范围的指定数量的元素。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Cmemory%3E\).md)|测试指定类的分配器对象之间是否不相等。|  
|[operator\=\=](../Topic/operator==%20\(%3Cmemory%3E\).md)|测试指定类的分配器对象之间是否相等。|  
|[运算符 \>\=](../Topic/operator%3E=%20\(%3Cmemory%3E\).md)|测试指定类的某一分配器对象是否大于或等于另一个分配器对象。|  
|[运算符 \<](../Topic/operator%3C%20\(%3Cmemory%3E\).md)|测试指定类的某一对象是否小于另一个对象。|  
|[运算符 \<\=](../Topic/operator%3C=%20\(%3Cmemory%3E\).md)|测试指定类的某一对象是否小于或等于另一个对象。|  
|[运算符 \>](../Topic/operator%3E%20\(%3Cmemory%3E\).md)|测试指定类的某一对象是否大于另一个对象。|  
|[运算符 \<\<](../Topic/operator%3C%3C%20\(%3Cmemory%3E\).md)|`shared_ptr` 插入器。|  
  
### 类  
  
|||  
|-|-|  
|[分配器](../standard-library/allocator-class.md)|此模板类描述一个对象，用于管理 **Type** 类对象数组的存储分配和释放。|  
|[allocator\_traits](../standard-library/allocator-traits-class.md)|描述一个对象，用于确定支持分配器的容器所需要的全部信息。|  
|[auto\_ptr](../standard-library/auto-ptr-class.md)|此模板类描述一个对象，用于存储指向 **Type \*** 类分配对象的指针，此指针可确保当它的封闭 auto\_ptr 被销毁后，将会删除它所指向的对象。|  
|[bad\_weak\_ptr](../standard-library/bad-weak-ptr-class.md)|报告不良的 weak\_ptr 异常。|  
|[enabled\_shared\_from\_this](../standard-library/enable-shared-from-this-class.md)|帮助生成一个 `shared_ptr`。|  
|[pointer\_traits](../standard-library/pointer-traits-struct.md)|提供模板类 `allocator_traits` 对象所需信息，用于描述一个采用指针类型 `Ptr` 的分配器。|  
|[raw\_storage\_iterator](../standard-library/raw-storage-iterator-class.md)|一种所提供的适配器类，使算法能够将它们的结果存储到未初始化的内存中。|  
|[shared\_ptr](../standard-library/shared-ptr-class.md)|将引用计数智能指针回绕在动态分配的对象周围。|  
|[unique\_ptr](../standard-library/unique-ptr-class.md)|存储指向拥有的对象的指针。  指针不归任何其他 `unique_ptr` 所拥有。  当所有者被销毁后，`unique_ptr` 也会被销毁。|  
|[weak\_ptr](../standard-library/weak-ptr-class.md)|回绕弱链接指针。|  
  
### 专用化  
  
|||  
|-|-|  
|[allocator\<void\>](../standard-library/allocator-void-class.md)|一种针对 void 类型进行的模板类分配器专用化，用于定义在此专用化上下文中有意义的成员类型。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)