---
title: 如何：创建和使用 weak_ptr 实例
ms.custom: how-to
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: 63eed40117d1a79c69bd05e5bd1503d4222f556d
ms.sourcegitcommit: af4ab63866ed09b5988ed53f1bb6996a54f02484
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787080"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>如何：创建和使用 weak_ptr 实例
有时对象必须存储一种可访问 `shared_ptr` 的基础对象又不导致其引用计数递增的方法。通常 `shared_ptr` 实例之间存在循环引用时会出现这种情况。最佳设计是尽可能避免共享指针的所有权。但如果必须具有共享所有权的 `shared_ptr`，请避免它们之间存在循环引用。如果循环引用不可避免，或出于某种原因，使用循环引用更合适，请使用 `weak_ptr` 为一个或多个所有者提供对另一个 `shared_ptr` 的弱引用。通过使用 `weak_ptr`，可以创建 `shared_ptr`，它可联接到一组现有的相关实例，前提是基础内存资源仍有效。`weak_ptr` 本身不参与引用计数，因此，它无法阻止引用计数计为零。但可使用 `weak_ptr` 来尝试获取初始化时用使用的 `shared_ptr` 的新副本。如果内存已删除，会引发 `bad_weak_ptr` 异常。如果内存仍有效，新的共享指针会递增引用计数，保证内存在 `shared_ptr` 变量保持在作用域内时一直有效。
有时对象必须存储一种可访问 `shared_ptr` 的基础对象又不导致其引用计数递增的方法。 通常 `shared_ptr` 实例之间存在循环引用时会出现这种情况。
最佳设计是尽可能避免共享指针的所有权。 但如果必须具有共享所有权的 `shared_ptr`，请避免它们之间存在循环引用。 如果循环引用不可避免，或出于某种原因，使用循环引用更合适，请使用 `weak_ptr` 为一个或多个所有者提供对另一个 `shared_ptr` 的弱引用。 通过使用 `weak_ptr`，可以创建 `shared_ptr`，它可联接到一组现有的相关实例，前提是基础内存资源仍有效。           `weak_ptr` 本身不参与引用计数，因此，它无法阻止引用计数计为零。 但可使用 `weak_ptr` 来尝试获取初始化时用使用的 `shared_ptr` 的新副本。 如果内存已删除，会引发 `bad_weak_ptr` 异常。 如果内存仍有效，新的共享指针会递增引用计数，保证内存在 `shared_ptr` 变量保持在作用域内时一直有效。

## <a name="example"></a>示例

下面的代码示例演示了一个用`weak_ptr`来确保正确删除具有循环依赖关系的对象的情况。 当你查看该示例时, 假定它是在考虑了替代解决方案之后创建的。 `Controller`对象表示计算机进程的某个方面, 它们独立运行。 每个控制器都必须能够随时查询其他控制器的状态, 并且每个控制器都包含一个专用`vector<weak_ptr<Controller>>`于此目的。 每个向量都包含一个循环引用, 因此`weak_ptr`使用的`shared_ptr`是实例, 而不是。

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
Status of 0 = On
Status of 1 = On
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

可试验一下，将向量 `others` 修改为 `vector<shared_ptr<Controller>>`，然后查看输出，注意，`TestRun` 返回时，没有析构函数被调用。

## <a name="see-also"></a>请参阅

[智能指针（现代 C++）](../cpp/smart-pointers-modern-cpp.md)
