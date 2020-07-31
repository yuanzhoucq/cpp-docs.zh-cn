---
title: from_chars_result 结构
ms.date: 7/23/2020
f1_keywords:
- std::from_chars_result
helpviewer_keywords:
- from_chars_result class
- from_chars_result structure
ms.openlocfilehash: 5a5dcfe6e5b59644e6ebf55d68ce43975e7d3c9d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215759"
---
# <a name="from_chars_result-struct"></a>from_chars_result 结构

## <a name="syntax"></a>语法

```cpp
struct from_chars_result {
    const char* ptr;
    errc ec;
};
```

|成员|描述|
|--|--|
|`ptr`| 如果 `ec` 等于 `errc{}` ，则转换成功，并 `ptr` 指向第一个不属于可识别数量的字符。 |
|`ec` | 转换错误代码。 有关特定的错误代码，请参阅 [`errc`](system-error-enums.md#errc) 。|

### <a name="remarks"></a>备注

例如： `"1729cats"` 作为十进制整数进行分析将会成功，并且 `ptr` 会将 `'c'` 其指向第一个非数字，也就是的结尾 `"1729"` 。

如果没有任何字符匹配数字模式， `from_chars_result.ptr` 则指向 `first` ，并 `from_chars_result.ec` 为 `errc::invalid_argument` 。

如果只有一些字符与数字模式匹配，则 `from_chars_result.ptr` 指向第一个不与模式匹配的字符， `last` 如果所有字符均匹配，则为参数的值。

如果分析的值无法满足转换类型的范围， `from_chars_result.ec` 则为 `errc::result_out_of_range` 。

## <a name="requirements"></a>要求

**标头：**\<charconv>

**命名空间:** std

**编译器选项：** /std： c + + 17 或更高版本是必需的

## <a name="see-also"></a>另请参阅

[from_chars](charconv-functions.md#from_chars)
