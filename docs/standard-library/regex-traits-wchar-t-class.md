---
title: regex_traits&lt;wchar_t&gt; 类
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_traits<wchar_t>
helpviewer_keywords:
- regex_traits<wchar_t> class
ms.assetid: 288d6fdb-fb8e-4a4d-904a-53916be7f95b
ms.openlocfilehash: dd0b54470f026635c1e09829f37d02bbe8b3f0c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217553"
---
# <a name="regex_traitsltwchar_tgt-class"></a>regex_traits&lt;wchar_t&gt; 类

的专用 `regex_traits` 化 **`wchar_t`** 。

## <a name="syntax"></a>语法

```cpp
template <>
class regex_traits<wchar_t>
```

## <a name="remarks"></a>备注

类是对类型元素的类模板[regex_traits](../standard-library/regex-traits-class.md)的显式专用化 **`wchar_t`** （以便它可以充分利用操作此类型对象的库函数）。

## <a name="requirements"></a>要求

**标头：**\<regex>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[\<regex>](../standard-library/regex.md)\
[regex_constants 类](../standard-library/regex-constants-class.md)\
[regex_error 类](../standard-library/regex-error-class.md)\
[\<regex>函数](../standard-library/regex-functions.md)\
[regex_iterator 类](../standard-library/regex-iterator-class.md)\
[\<regex>运算符](../standard-library/regex-operators.md)\
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)\
[regex_traits 类](../standard-library/regex-traits-class.md)\
[\<regex>typedef](../standard-library/regex-typedefs.md)
