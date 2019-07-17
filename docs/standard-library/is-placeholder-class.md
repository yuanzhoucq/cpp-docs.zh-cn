---
title: is_placeholder 类
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 9fa7d4aaade6244fe26f89f3a667598d39471a47
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245150"
---
# <a name="isplaceholder-class"></a>is_placeholder 类

测试类型是否为占位符。

## <a name="syntax"></a>语法

结构 is_placeholder {静态 const int 值;};

## <a name="remarks"></a>备注

如果类型 `Ty` 不是占位符，则常量值 `value` 为 0；否则，其值为其所绑定的函数调用参数的位置。 使用它来确定第 N 个占位符 `_N` 的值 `N`。

## <a name="example"></a>示例

```cpp
// std__functional__is_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

using namespace std::placeholders;

template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}
```

```Output
0
3
```
