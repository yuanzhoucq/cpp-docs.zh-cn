---
title: "如何：创建和使用 shared_ptr 实例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：创建和使用 shared_ptr 实例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`shared_ptr` 的类型是C \+ \+标准库中一个聪明的指针，是为多个拥有者管理内存中对象的生命周期而设计的。  在你初始化一个 `shared_ptr` 后，你可以复制它，把函数参数的值递给它，并把它分配给其它 `shared_ptr` 实例。  所有实例指向同一个对象，并共享访问一个“控制块”，即每当一个新的 `shared_ptr` 被添加时，递增和递减引用计数，超出范围，则复位。  当引用计数到达零时，控制块删除内存资源和自身。  
  
 下图显示了指向一个内存位置的几个 `shared_ptr` 实例。  
  
 [![共享指针](../Image/shared_ptr.png "shared\_ptr")](assetId:///9785ad08-31d8-411a-86a9-fb9cd9684c27)  
  
## 示例  
 无论什么时候，当内存资源被第一次被创建时，就使用函数 [make\_shared](../Topic/make_shared%20\(%3Cmemory%3E\).md) 创建一个新的 `shared_ptr`。  `make_shared`异常安全。  它使用同一调用分配的内存控制块和资源从而减少构造开销。  如果你不使用 `make_shared`，那么在把它传递给 `shared_ptr` 的构造函数之前，你必须使用一个明确的新表达式创建的对象。  下面的例子显示了在新对象中声明和初始化一个 `shared_ptr` 的各种方式。  
  
 [!code-cpp[stl_smart_pointers#1](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]  
  
## 示例  
 下面的示例演示如何声明和初始化一个已经被分配了另一个 `shared_ptr` 的对象共享所有权的 `shared_ptr` 的实例。  假设 `sp2` 是一个初始化的 `shared_ptr`。  
  
 [!code-cpp[stl_smart_pointers#2](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]  
  
## 示例  
 当您使用算法复制元素时，`shared_ptr` 的也是很有用的标准模板库（STL）。  你可以把元素包装在 `shared_ptr` 里，然后将其复制到其他容器，只要你需要它，底层的内存始终是有效的。  以下示例演示如何使用 `replace_copy_if` 算法来创建一个 `shared_ptr` 的实例以及如何在一个向量上进行使用。  
  
 [!code-cpp[stl_smart_pointers#4](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]  
  
## 示例  
 你可以用 `dynamic_pointer_cast`， `static_pointer_cast` 和 `const_pointer_cast` 来转换`shared_ptr`。  这些函数的操作类似 `dynamic_cast`， `static_cast` 和 `const_cast`。  下面的示例演示如何测试在基类的 `shared_ptr` 向量中的每个元素的派生类，，然后复制元素，并显示它们的信息。  
  
 [!code-cpp[stl_smart_pointers#5](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]  
  
## 示例  
 你可以用下列方法把 `shared_ptr` 传递给另一个函数：  
  
-   向 `shared_ptr` 传递值。  调用复制构造函数，递增引用计数，并把被调用方当做所有者。  还有就是在这次操作中有少量的开销，这很大程度上取决于你传递了多少 `shared_ptr` 对象。  当调用方和被调用方之间的代码协定 \(隐式或显式\) 要求被调用方是所有者，使用此选项。  
  
-   通过引用或常量引用来传递 `shared_ptr`。  在这种情况下，引用计数不增加，并且只要调用方不超出范围，被调用方就可以访问指针。  或者，被调用方可以决定创建一个基于引用的 `shared_ptr`，从而成为一个共享所有者。  当调用者并不知道被被调用方，或当您必须传递一个 `shared_ptr`，并希望避免由于性能原因的复制操作，请使用此选项。  
  
-   通过底层的指针或引用底层的对象。  这使得被调用方使用对象，但不使共享所有权或扩展生存期。  如果被调用方从原始指针创建一个 `shared_ptr`，则新的 `shared_ptr` 是独立于原来的，且没有控制底层的资源。  当调用方和被调用方之间的协定中明确规定调用者保留 `shared_ptr` 生存期的所有权，则使用此选项。  
  
-   当您决定如何传递一个 `shared_ptr`时，确定被调用方是否有共享基础资源的所有权。  一个“所有者”就是只要它需要就可以使用底层资源的对象或函数。  如果调用方必须保证被调用方可以在其（函数）生存期以外扩展指针的生存期，请使用第一个选项。  如果您不关心被调用方是否扩展生存期，则通过引用传递并让被调用方复制它。  
  
-   如果不得不允许帮助程序函数访问底层指针，并且您知道帮助程序函数将使用指针且在调用函数返回前先返回，则该函数不必共享底层指针的所有权。  仅仅是在调用方的 `shared_ptr` 的生存期内允许访问指针。  在这种情况下，通过引用来传递 `shared_ptr`，通过原始指针或引用的基本对象都是安全的。  通过此方式提供一个小的性能改进，并且还有助于表示程序的意图。  
  
-   有时，例如在一个 `std:vector<shared_ptr<T>>`中，您可能必须对传递每个 `shared_ptr` 给lambda表达式体或命名函数对象。  如果lambda或函数没有存储指针，则通过引用传递 `shared_ptr`，以避免调用拷贝构造函数的每个元素。  
  
 [!CODE [stl_smart_pointers#6](../CodeSnippet/VS_Snippets_Cpp/stl_smart_pointers#6)]  
  
## 示例  
 下面的示例显示 `shared_ptr` 如何重载多种比较操作符，以使由 `shared_ptr` 实例所拥有的内存指针的比较。  
  
 [!code-cpp[stl_smart_pointers#3](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]  
  
## 请参阅  
 [智能指针](../cpp/smart-pointers-modern-cpp.md)