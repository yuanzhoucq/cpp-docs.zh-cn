---
title: 如何：创建和使用 weak_ptr 实例
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
# <a name="how-to-create-and-use-weak_ptr-instances"></a>如何：创建和使用 weak_ptr 实例

有时，对象必须存储一种方法来访问[shared_ptr](../standard-library/shared-ptr-class.md)的基础对象，而不会导致引用计数递增。 通常情况下，在 `shared_ptr` 实例之间具有循环引用时，会发生这种情况。

最佳设计是避免在任何时候都能实现指针的共享所有权。 但是，如果您必须拥有 `shared_ptr` 实例的共享所有权，请避免它们之间的循环引用。 如果无法避免循环引用，或者出于某种原因更可取，则使用[weak_ptr](../standard-library/weak-ptr-class.md)向一个或多个所有者提供对另一 `shared_ptr`的弱引用。 通过使用 `weak_ptr`，可以创建加入到现有相关实例集的 `shared_ptr`，但前提是基础内存资源仍有效。 `weak_ptr` 本身并不参与引用计数，因此它无法阻止引用计数转到零。 不过，你可以使用 `weak_ptr` 来尝试获取已初始化的 `shared_ptr` 的新副本。 如果已删除内存，则 `weak_ptr`的布尔运算符将返回 `false`。 如果内存仍有效，新的共享指针会递增引用计数，并保证只要 `shared_ptr` 变量保持在范围内，内存就有效。

## <a name="example"></a>示例

下面的代码示例演示了一个示例，该示例使用 `weak_ptr` 来确保正确删除具有循环依赖关系的对象。 当你查看该示例时，假定它是在考虑了替代解决方案之后创建的。 `Controller` 对象表示计算机进程的某个方面，它们独立运行。 每个控制器都必须能够随时查询其他控制器的状态，并且每个控制器都包含用于此目的的专用 `vector<weak_ptr<Controller>>`。 每个向量都包含一个循环引用，因此使用 `weak_ptr` 实例，而不是 `shared_ptr`。

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

作为试验，将 vector `others` 修改为 `vector<shared_ptr<Controller>>`，然后在输出中，请注意，`TestRun` 返回时不会调用析构函数。

## <a name="see-also"></a>另请参阅

[智能指针（现代 C++）](../cpp/smart-pointers-modern-cpp.md)
