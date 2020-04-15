---
title: regex_error 类
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: f8f3c88c1b203ed7fcea148843fa99590e27b888
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331868"
---
# <a name="regex_error-class"></a>regex_error 类

报告错误的 basic_regex 对象。

## <a name="syntax"></a>语法

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>备注

该类描述一个异常对象，引发该异常的目的是为报告一个构造中的错误或 `basic_regex` 对象的使用错误。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[regex_error](#regex_error)|构造对象。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[代码](#code)|返回错误代码。|

## <a name="requirements"></a>要求

**标头：** \<regex 1>

**命名空间:** std

## <a name="example"></a>示例

```cpp
// std__regex__regex_error.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex_error paren(std::regex_constants::error_paren);

    try
        {
        std::regex rx("(a");
        }
    catch (const std::regex_error& rerr)
        {
        std::cout << "regex error: "
            << (rerr.code() == paren.code() ? "unbalanced parentheses" : "")
            << std::endl;
        }
    catch (...)
        {
        std::cout << "unknown exception" << std::endl;
        }

    return (0);
    }
```

```Output
regex error: unbalanced parentheses
```

## <a name="regex_errorcode"></a><a name="code"></a>regex_error：代码

返回错误代码。

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>备注

成员函数将返回传递给对象的构造函数的值。

## <a name="regex_errorregex_error"></a><a name="regex_error"></a>regex_error：：regex_error

构造对象。

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>参数

*错误*\
错误代码。

### <a name="remarks"></a>备注

构造函数构造保存值*误差*的对象。

## <a name="see-also"></a>另请参阅

[\<正则>](../standard-library/regex.md)\
[regex_constants类](../standard-library/regex-constants-class.md)\
[\<正则表达式>函数](../standard-library/regex-functions.md)\
[regex_iterator类](../standard-library/regex-iterator-class.md)\
[\<正则>运算符](../standard-library/regex-operators.md)\
[regex_token_iterator类](../standard-library/regex-token-iterator-class.md)\
[regex_traits类](../standard-library/regex-traits-class.md)\
[\<正则>类型](../standard-library/regex-typedefs.md)
