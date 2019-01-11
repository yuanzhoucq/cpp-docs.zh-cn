---
title: 如何：创建和使用共享 weak_ptr 实例
ms.custom: how-to
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: 1a0e2880e97a77a0c9975553631a6024072745f0
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220317"
---
# <a name="how-to-create-and-use-weakptr-instances"></a>如何：创建和使用共享 weak_ptr 实例

有时对象必须存储一种方法访问的基础对象`shared_ptr`而不会导致引用计数会递增。 当你具有之间进行循环引用时，通常情况下，出现这种情况`shared_ptr`实例。

最佳的设计是为了避免共享的所有权的指针，在可能的情况。 但是，如果您必须具有共享所有权的`shared_ptr`情况下，避免之间进行循环引用。 当循环引用不可避免的或甚至更可取出于某种原因，请使用`weak_ptr`为一个或多个所有者提供对另一个的弱引用`shared_ptr`。 通过使用`weak_ptr`，可以创建`shared_ptr`，可以将其联接到一组现有的相关实例，但仅基础内存资源是否仍有效。 一个`weak_ptr`本身不参与引用计数，并因此，它无法阻止引用计数转到为零。 但是，可以使用`weak_ptr`来尝试获取的新副本`shared_ptr`与它已初始化。 如果内存已被删除，`bad_weak_ptr`引发异常。 如果内存仍有效，新的共享的指针递增引用计数，并保证内存将生效，只要`shared_ptr`变量保持在范围内。

## <a name="example"></a>示例

下面的代码示例显示了一种情况其中`weak_ptr`用于确保正确删除循环依赖项的对象。 检查示例时，假定它创建仅在考虑备用解决方案后。 `Controller`对象表示处理的某些方面，它们将独立运行。 每个控制器必须能够在任何时候，查询其他控制器的状态和每个包含私有`vector<weak_ptr<Controller>>`实现此目的。 每个向量包含循环引用，因此`weak_ptr`而不是使用实例`shared_ptr`。

[!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]

```Output
Creating Controller0
Creating Controller1
Creating Controller2
Creating Controller3
Creating Controller4
push_back to v[0]: 1
push_back to v[0]: 2
push_back to v[0]: 3
push_back to v[0]: 4
push_back to v[1]: 0
push_back to v[1]: 2
push_back to v[1]: 3
push_back to v[1]: 4
push_back to v[2]: 0
push_back to v[2]: 1
push_back to v[2]: 3
push_back to v[2]: 4
push_back to v[3]: 0
push_back to v[3]: 1
push_back to v[3]: 2
push_back to v[3]: 4
push_back to v[4]: 0
push_back to v[4]: 1
push_back to v[4]: 2
push_back to v[4]: 3
use_count = 1
Status of 1 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = O
nStatus of 1 = On
Status of 2 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 3 = On
Destroying Controller0
Destroying Controller1
Destroying Controller2
Destroying Controller3
Destroying Controller4
Press any key
```

试验一下，修改向量`others`要`vector<shared_ptr<Controller>>`，然后在输出中，请注意，在不析构函数进行调用时`TestRun`返回。

## <a name="see-also"></a>请参阅

[智能指针（现代 C++）](../cpp/smart-pointers-modern-cpp.md)
