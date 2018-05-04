---
title: __func__ |Microsoft 文档
ms.custom: ''
ms.date: 10/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __func__
dev_langs:
- C++
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d78a249fe5b111c17c29895edcdc3fa5ba2f27a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="func"></a>__func__

**(C++ 11)** 的预定义的标识符 & #95; & #95; func #95; & #95; 隐式定义为包含封闭函数的未限定和未修饰名称的字符串。 & #95; & #95; func & #95; & #95;由 C++ 标准规定，且不是一个 Microsoft 扩展。

## <a name="syntax"></a>语法

```cpp
__func__
```

## <a name="return-value"></a>返回值

返回以 null 结尾 const char 字符数组，其中包含函数名称。

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