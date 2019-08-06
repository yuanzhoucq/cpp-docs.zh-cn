---
title: regex_error 类
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: 52b6bfd74a08200f7d924d2601b85718a941dd85
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451652"
---
# <a name="regexerror-class"></a>regex_error 类

报告错误的 basic_regex 对象。

## <a name="syntax"></a>语法

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>备注

该类描述一个异常对象，引发该异常的目的是为报告一个构造中的错误或 `basic_regex` 对象的使用错误。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[regex_error](#regex_error)|构造对象。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[代码](#code)|返回错误代码。|

## <a name="requirements"></a>要求

**标头：** \<regex 1>

**命名空间：** std

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

## <a name="code"></a>  regex_error::code

返回错误代码。

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>备注

成员函数将返回传递给对象的构造函数的值。

## <a name="regex_error"></a>  regex_error::regex_error

构造对象。

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>参数

*条*\
错误代码。

### <a name="remarks"></a>备注

构造函数构造保存值*错误*的对象。

## <a name="see-also"></a>请参阅

[\<regex>](../standard-library/regex.md)\
[regex_constants 类](../standard-library/regex-constants-class.md)\
[\<regex > 函数](../standard-library/regex-functions.md)\
[regex_iterator 类](../standard-library/regex-iterator-class.md)\
[\<regex > 运算符](../standard-library/regex-operators.md)\
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)\
[regex_traits 类](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
