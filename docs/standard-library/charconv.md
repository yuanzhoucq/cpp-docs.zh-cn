---
title: '&lt;charconv&gt;'
ms.date: 07/22/2020
f1_keywords:
- <charconv>
helpviewer_keywords:
- charconv header
ms.openlocfilehash: 59807749105512e0eb61acfdf60ef463febbc3a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230189"
---
# <a name="ltcharconvgt"></a>&lt;charconv&gt;

快速将字符序列转换为整数或浮点值，另一种方法。
使用此库的一种方法是在 JSON 和文本文件中写入浮点值并对其进行往返。

转换函数针对性能进行了优化，并且还支持最短的往返行为。 最短往返行为表示将数字转换为字符时，只写出足够的精度，以便在将这些字符转换回浮点时恢复原始数字。 没有其他 CRT 或 STL 函数提供此功能。

使用库的一些优点 `<charconv>` 包括：

- 表示数值的字符序列不需要以 null 值终止。 同样，将数字转换为字符时，结果不会以 null 结尾。
- 转换函数不分配内存。 所有情况下都拥有缓冲区。
- 转换函数不会引发。 它们返回包含错误信息的结构。
- 转换不区分运行时舍入模式。
- 转换不识别区域设置。 它们始终将小数点打印并分析为使用逗号的区域设置，而不是 "，"。

## <a name="requirements"></a>要求

**标头：**\<charconv>

**命名空间:** std

/std： c + + 17 或更高版本是必需的。

## <a name="members"></a>成员

### <a name="types"></a>类型

| 类型 | 描述 |
|-|:-|
| [chars_format](chars-format-class.md) | 指定格式设置类型，例如科学、十六进制等。 |
| [from_chars_result](from-chars-result-structure.md) | 保存转换的结果 `from_chars` 。 |
| [to_chars_result](to-chars-result-structure.md) | 保存转换的结果 `to_chars` 。 |

### <a name="functions"></a>函数

| 函数 | 描述 |
|-|:-|
| [from_chars](charconv-functions.md#from_chars) | 将字符转换为整数、float 或 double。 |
| [to_chars](charconv-functions.md#to_chars)| 将 integer、float 或 double 转换为字符。 |

## <a name="see-also"></a>另请参阅

[头文件引用](cpp-standard-library-header-files.md)

