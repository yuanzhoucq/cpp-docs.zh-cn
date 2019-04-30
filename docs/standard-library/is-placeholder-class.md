---
title: is_placeholder 类
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 2c7848c88194a9b541867b26ffe27764ad862503
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413627"
---
# <a name="isplaceholder-class"></a>is_placeholder 类

测试类型是否为占位符。

## <a name="syntax"></a>语法

struct is_placeholder { static const int value; };

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

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[_1 对象](../standard-library/1-object.md)<br/>
