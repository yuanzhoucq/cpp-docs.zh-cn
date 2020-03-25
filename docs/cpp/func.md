---
title: func
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: 8e94caffe120c325478d8b4f24c1915a516d69f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179817"
---
# <a name="__func__"></a>func

**（C + + 11）** 预定义的&#95; &#95;标识符&#95; &#95; func 隐式定义为包含封闭函数的非限定和未修饰名称的字符串。 & #95; & #95; func & #95; & #95;由 C++ 标准规定，且不是一个 Microsoft 扩展。

## <a name="syntax"></a>语法

```cpp
__func__
```

## <a name="return-value"></a>返回值

返回一个以 null 结尾的 const char 字符数组，其中包含函数名称。

## <a name="example"></a>示例

```cpp
#include <string>
#include <iostream>

namespace Test
{
    struct Foo
    {
        static void DoSomething(int i, std::string s)
        {
           std::cout << __func__ << std::endl; // Output: DoSomething
        }
    };
}

int main()
{
    Test::Foo::DoSomething(42, "Hello");

    return 0;
}
```

## <a name="requirements"></a>要求

C++11
