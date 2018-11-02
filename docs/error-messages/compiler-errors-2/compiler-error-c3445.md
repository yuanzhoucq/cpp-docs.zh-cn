---
title: 编译器错误 C3445
ms.date: 04/10/2017
f1_keywords:
- C3445
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
ms.openlocfilehash: 2eddeb5a56c953ca0864e29187fbe28c53bdee24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574208"
---
# <a name="compiler-error-c3445"></a>编译器错误 C3445

> 复制列表初始化的 '*类型*不能使用的显式构造函数

根据 ISO 标准 C + + 17 中，编译器需要考虑用于重载决策中复制列表初始化的显式构造函数，但如果实际选择该重载必须引发错误。

从 Visual Studio 2017 中，编译器找找不到由 Visual Studio 2015 的错误与对象创建相关使用初始值设定项列表。 这些错误可能会导致崩溃或未定义在运行时的行为。

## <a name="example"></a>示例

下面的示例生成 C3445。

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

若要更正此错误，请改为使用直接初始化：

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```
