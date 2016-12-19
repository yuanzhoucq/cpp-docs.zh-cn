---
title: "如何：创建和使用共享 weak_ptr 实例 | Microsoft Docs"
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
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：创建和使用共享 weak_ptr 实例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有时对象必须存储一种方法，用来在不引起引用计数增加的情况下访问 `shared_ptr` 的基础对象。  通常，当您在 `shared_ptr` 实例之间循环引用时，就会出现此情况。  
  
 最佳的设计能够尽可能地避免指针具有共享所有权。  但是，如果您必须具有共享的 `shared_ptr` 实例所有权，请避免在实例之间进行循环引用。  如果循环引用不可避免，甚至由于某种原因而更为可取，请使用 `weak_ptr` 为一个或多个所有者提供对其他 `shared_ptr` 的弱引用。  使用 `weak_ptr`，您可以创建连接到现有相关实例组的 `shared_ptr`，但仅当基础内存资源有效时才行。  `weak_ptr` 本身并不参与引用计数，因此，它无法阻止引用计数转到为零。  但是，您可以使用 `weak_ptr` 来尝试获取 `shared_ptr` 的新副本，通过使用该副本进行初始化。  如果内存已被删除，则会引发 **bad\_weak\_ptr** 异常。  如果内存仍有效，则新的共享指针会递增引用计数，并确保只要 `shared_ptr` 变量保持在范围内，内存就有效。  
  
## 示例  
 下面的代码示例演示了使用 `weak_ptr` 以确保正确删除循环依赖关系对象的实例。  检查示例时，假定它是仅在考虑备用解决方案后才创建的。  `Controller` 对象表示设备处理的某个方面，并且能独立运行。  每个控制器必须能够在任何时间查询其他控制器的状态，因此，每个控制器包含私有  `vector<weak_ptr<Controller>>`。  由于每个向量包含一个循环引用，因此使用 `weak_ptr` 实例而不是 `shared_ptr`。  
  
 [!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]  
  
  **创建 Controller0**  
**创建 Controller1**  
**创建 Controller2**  
**创建 Controller3**  
**创建 Controller4**  
**push\_back 到 v\[0\]: 1**  
**push\_back 到 v\[0\]: 2**  
**push\_back 到 v\[0\]: 3**  
**push\_back 到 v\[0\]: 4**  
**push\_back 到 v\[1\]: 0**  
**push\_back 到 v\[1\]: 2**  
**push\_back 到 v\[1\]: 3**  
**push\_back 到 v\[1\]: 4**  
**push\_back 到 v\[2\]: 0**  
**push\_back 到 v\[2\]: 1**  
**push\_back 到 v\[2\]: 3**  
**push\_back 到 v\[2\]: 4**  
**push\_back 到 v\[3\]: 0**  
**push\_back 到 v\[3\]: 1**  
**push\_back 到 v\[3\]: 2**  
**push\_back 到 v\[3\]: 4**  
**push\_back 到 v\[4\]: 0**  
**push\_back 到 v\[4\]: 1**  
**push\_back 到 v\[4\]: 2**  
**push\_back 到 v\[4\]: 3**  
**use\_count \= 1**  
**1 的状态 \= 打开**  
**2 的状态 \= 打开**  
**3 的状态 \= 打开**  
**4 的状态 \= 打开**  
**use\_count \= 1**  
**0 的状态 \= 打开**  
**2 的状态 \= 打开**  
**3 的状态 \= 打开**  
**4 的状态 \= 打开**  
**use\_count \= 1**  
**0 的状态 \= 打开**  
**1 的状态 \= 打开**  
**3 的状态 \= 打开**  
**4 的状态 \= 打开**  
**use\_count \= 1**  
**0 的状态 \= 打开**  
**1 的状态 \= 打开**  
**2 的状态 \= 打开**  
**4 的状态 \= 打开**  
**use\_count \= 1**  
**0 的状态 \= 打开**  
**1 的状态 \= 打开**  
**2 的状态 \= 打开**  
**3 的状态 \= 打开**  
**正在销毁 Controller0**  
**正在销毁 Controller1**  
**正在销毁 Controller2**  
**正在销毁 Controller3**  
**正在销毁 Controller4**  
**按任意键** 作为练习，将向量 `others` 修改为 `vector<shared_ptr<Controller>>`，然后在输出中，注意当 `TestRun` 返回时，未调用析构函数。  
  
## 请参阅  
 [智能指针](../cpp/smart-pointers-modern-cpp.md)