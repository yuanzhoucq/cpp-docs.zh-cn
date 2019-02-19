---
title: 对象拥有资源 (RAII)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f86b484e-5a27-4c3b-a92a-dfaa5dd6d93a
ms.openlocfilehash: 5705fc1996343141b13e37d1267b2e8c981c1eba
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220421"
---
# <a name="objects-own-resources-raii"></a>对象拥有资源 (RAII)

请确保对象拥有资源。 此原则也称“资源获取即是初始化”，简称“RAII”。

## <a name="example"></a>示例

将"新"的每个对象作为构造函数参数传递给另一个命名对象，该对象拥有它 (几乎总是 unique_ptr)。

```cpp
void f() {
    unique_ptr<widget> p( new widget() );
    my_class x( new widget() );
    // ...
} // automatic destruction and deallocation for both widget objects
  // automatic exception safety, as if "finally { p->dispose(); x.w.dispose(); }"
```

一定会立即传递给拥有它的另一个对象的任何新的资源。

```cpp
void g() {
    other_class y( OpenFile() );
    // ...
} // automatic closing and release for file resource
  // automatic exception safety, as if "finally { y.file.dispose(); }"
```

## <a name="see-also"></a>请参阅

[欢迎回到 C++（现代 C++）](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
