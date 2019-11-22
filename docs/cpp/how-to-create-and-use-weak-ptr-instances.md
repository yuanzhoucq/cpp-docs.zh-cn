---
title: 'How to: Create and use weak_ptr instances'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: 32e8d64fdb6449f1d40aec4161bfda54987ca66a
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245601"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>How to: Create and use weak_ptr instances
有时对象必须存储一种可访问 `shared_ptr` 的基础对象又不导致其引用计数递增的方法。通常 `shared_ptr` 实例之间存在循环引用时会出现这种情况。最佳设计是尽可能避免共享指针的所有权。但如果必须具有共享所有权的 `shared_ptr`，请避免它们之间存在循环引用。如果循环引用不可避免，或出于某种原因，使用循环引用更合适，请使用 `weak_ptr` 为一个或多个所有者提供对另一个 `shared_ptr` 的弱引用。通过使用 `weak_ptr`，可以创建 `shared_ptr`，它可联接到一组现有的相关实例，前提是基础内存资源仍有效。`weak_ptr` 本身不参与引用计数，因此，它无法阻止引用计数计为零。但可使用 `weak_ptr` 来尝试获取初始化时用使用的 `shared_ptr` 的新副本。如果内存已删除，会引发 `bad_weak_ptr` 异常。如果内存仍有效，新的共享指针会递增引用计数，保证内存在 `shared_ptr` 变量保持在作用域内时一直有效。
Sometimes an object must store a way to access the underlying object of a [shared_ptr](../standard-library/shared-ptr-class.md) without causing the reference count to be incremented. Typically, this situation occurs when you have cyclic references between `shared_ptr` instances.
The best design is to avoid shared ownership of pointers whenever you can. However, if you must have shared ownership of `shared_ptr` instances, avoid cyclic references between them. When cyclic references are unavoidable, or even preferable for some reason, use [weak_ptr](../standard-library/weak-ptr-class.md) to give one or more of the owners a weak reference to another `shared_ptr`. By using a `weak_ptr`, you can create a `shared_ptr` that joins to an existing set of related instances, but only if the underlying memory resource is still valid. A `weak_ptr` itself does not participate in the reference counting, and therefore, it cannot prevent the reference count from going to zero. However, you can use a `weak_ptr` to try to obtain a new copy of the `shared_ptr` with which it was initialized. If the memory has already been deleted, the `weak_ptr`'s bool operator returns `false`. If the memory is still valid, the new shared pointer increments the reference count and guarantees that the memory will be valid as long as the `shared_ptr` variable stays in scope.

## <a name="example"></a>示例

The following code example shows a case where `weak_ptr` is used to ensure proper deletion of objects that have circular dependencies. As you examine the example, assume that it was created only after alternative solutions were considered. The `Controller` objects represent some aspect of a machine process, and they operate independently. Each controller must be able to query the status of the other controllers at any time, and each one contains a private `vector<weak_ptr<Controller>>` for this purpose. Each vector contains a circular reference, and therefore, `weak_ptr` instances are used instead of `shared_ptr`.

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

As an experiment, modify the vector `others` to be a `vector<shared_ptr<Controller>>`, and then in the output, notice that no destructors are invoked when `TestRun` returns.

## <a name="see-also"></a>请参阅

[智能指针（现代 C++）](../cpp/smart-pointers-modern-cpp.md)
