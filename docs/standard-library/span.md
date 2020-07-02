---
title: '&lt;格&gt;'
ms.date: 05/28/2020
f1_keywords:
- <span>
helpviewer_keywords:
- span header
ms.openlocfilehash: 27f27acfa84a3ccc42586593747e4657146cbe39
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813530"
---
# <a name="ltspangt"></a>&lt;格&gt;

`span`是一个视图，它是一系列连续的对象。 它提供快速且不安全的访问。 与 `vector` 或不同 `array` ，它不会 "拥有" 它提供访问权限的元素。

有关详细信息，请参阅[span 类](span-class.md)。 下面是如何使用范围的示例：

```cpp
#include <span>
#include <iostream>

void Show(std::span<int> someValues)
{
    // show values in reverse
    for (auto rIt = someValues.rbegin(); rIt != someValues.rend(); ++rIt)
    {
        std::cout << *rIt;
    }

    // show a subspan
    for (auto& i : someValues.subspan(1, 2))
    {
        std::cout << i;
    }
}

int main()
{
    int numbers[]{ 0,1,2,3,4 };
    Show(numbers); // note conversion from array to span
}
```

## <a name="requirements"></a>要求

**标头：**\<span>

**命名空间:** std

**编译器选项：** /std： c + + 最新

## <a name="members"></a>成员

### <a name="classes"></a>类

|||
|-|:-|
|[格](span-class.md)| 提供对一系列连续对象的视图。 |

### <a name="operators"></a>运算符

|||
|-|:-|
|[operator =](span-class.md#op_eq)| 跨度赋值 |
|[操作员\[\]](span-class.md#op_at)| 元素访问 |

### <a name="functions"></a>函数

|||
|-|:-|
| [as_bytes](span-functions.md#as_bytes)| 获取跨度的基础只读字节。 |
| [as_writable_bytes](span-functions.md#as_writable_bytes) | 获取跨度的基础字节。 |

### <a name="constants"></a>常量

|||
|-|:-|
| **dynamic_extent** | 指示范围大小在运行时确定，而不是在编译时确定。 如果范围中的元素数量在编译时是已知的，则会将其指定为 `Extent` 模板参数。 如果在运行时之前不知道该数字，请改为指定 `dynamic_extent` 。 |

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
