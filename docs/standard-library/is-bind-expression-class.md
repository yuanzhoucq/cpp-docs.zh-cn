---
title: is_bind_expression 类
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_bind_expression
helpviewer_keywords:
- is_bind_expression class
ms.assetid: 0715f9e9-2239-4778-a1cf-2c21f49dfd47
ms.openlocfilehash: f547b6f74a86612174cb0f510870171158678f7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519413"
---
# <a name="isbindexpression-class"></a>is_bind_expression 类

测试通过调用 `bind` 是否生成类型。

## <a name="syntax"></a>语法

模板<class Ty>结构 is_bind_expression {静态 const bool 值;};

## <a name="remarks"></a>备注

如果类型 `Ty` 是调用 `bind` 返回的类型，则常量成员 `value` 为 true，否则为 false。

## <a name="example"></a>示例

```cpp
// std__functional__is_bind_expression.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

template<class Expr>
void test_for_bind(const Expr&)
{
    std::cout << std::is_bind_expression<Expr>::value << std::endl;
}

int main()
{
    test_for_bind(3.0 * 3.0);
    test_for_bind(std::bind(square, 3));

    return (0);
}
```

```Output
0
1
```

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[bind](../standard-library/functional-functions.md#bind)<br/>
