---
title: "如何： 创建和使用共享 weak_ptr 实例 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e51e523540e14905bef17edd52205c4d2102afa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-and-use-weakptr-instances"></a>如何：创建和使用共享 weak_ptr 实例
有时对象必须存储用于访问的基础对象的方法`shared_ptr`而不会导致要递增的引用计数。 当之间的循环引用时，通常情况下，出现这种情况`shared_ptr`实例。  
  
 最佳设计是尽可能避免共享的所有权的指针。 但是，如果你必须具有共享所有权的`shared_ptr`情况下，避免它们之间的循环引用。 当循环引用不可避免的或甚至更可取的方法因某种原因，请使用`weak_ptr`为一个或多个所有者提供对另一个的弱引用`shared_ptr`。 通过使用`weak_ptr`，你可以创建`shared_ptr`，可以将其联接到一组现有的相关的实例，但仅基础的内存资源是否仍然有效。 A`weak_ptr`本身不参与引用计数，而因此，它不能阻止从转到零的引用计数。 但是，你可以使用`weak_ptr`来试图获得的新副本`shared_ptr`与初始化它。 如果已删除内存， **bad_weak_ptr**引发异常。 如果仍有效的内存，新的共享的指针递增引用计数，并保证内存才会生效，只要`shared_ptr`变量保持在范围内。  
  
## <a name="example"></a>示例  
 下面的代码示例演示一种情况其中`weak_ptr`用于确保正确删除具有循环依赖项的对象。 在您检查示例，假定它创建仅后考虑替代解决方案了。 `Controller`对象代表机过程中，某个方面，这些独立运行。 每个控制器必须能够在任何时候，查询的其他控制器的状态和每个包含私有`vector<weak_ptr<Controller>>`为此目的。 每个矢量包含循环引用，因此，`weak_ptr`而不是使用实例`shared_ptr`。  
  
 [!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]  
  
```Output  
Creating Controller0Creating Controller1Creating Controller2Creating Controller3Creating Controller4push_back to v[0]: 1push_back to v[0]: 2push_back to v[0]: 3push_back to v[0]: 4push_back to v[1]: 0push_back to v[1]: 2push_back to v[1]: 3push_back to v[1]: 4push_back to v[2]: 0push_back to v[2]: 1push_back to v[2]: 3push_back to v[2]: 4push_back to v[3]: 0push_back to v[3]: 1push_back to v[3]: 2push_back to v[3]: 4push_back to v[4]: 0push_back to v[4]: 1push_back to v[4]: 2push_back to v[4]: 3use_count = 1Status of 1 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 3 = OnDestroying Controller0Destroying Controller1Destroying Controller2Destroying Controller3Destroying Controller4Press any key  
```  
  
 进行试验，修改向量`others`要`vector<shared_ptr<Controller>>`，然后在输出中，记下，在没有析构函数进行调用时`TestRun`返回。  
  
## <a name="see-also"></a>请参阅  
 [智能指针](../cpp/smart-pointers-modern-cpp.md)