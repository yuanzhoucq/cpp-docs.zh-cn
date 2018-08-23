---
title: 编译器错误 C3445 |Microsoft 文档
ms.custom: ''
ms.date: 04/10/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3445
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c37f04b907183b883772fd144ae0179683f088f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256761"
---
# <a name="compiler-error-c3445"></a>编译器错误 C3445

> 复制列表的初始化的*类型*不能使用的显式构造函数

根据 ISO C + + 17 标准中，编译器需要考虑在副本列表初始化的重载决策的显式构造函数，但如果实际选择该重载，则必须引发错误。

从 Visual Studio 2017 年 1 开始，编译器找不使用初始值设定项列表与对象创建相关的错误，未找到由 Visual Studio 2015。 这些错误可能导致发生崩溃或未定义在运行时的行为。

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

若要更正错误，请改为使用直接初始化：

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
