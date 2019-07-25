---
title: regex_constants 类
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_constants
- regex/std::regex_constants::error_collate
- regex/std::regex_constants::error_ctype
- regex/std::regex_constants::error_escape
- regex/std::regex_constants::error_backref
- regex/std::regex_constants::error_brack
- regex/std::regex_constants::error_paren
- regex/std::regex_constants::error_brace
- regex/std::regex_constants::error_badbrace
- regex/std::regex_constants::error_range
- regex/std::regex_constants::error_space
- regex/std::regex_constants::error_badrepeat
- regex/std::regex_constants::error_complexity
- regex/std::regex_constants::error_stack
- regex/std::regex_constants::error_parse
- regex/std::regex_constants::error_syntax
- regex/std::regex_constants::match_default
- regex/std::regex_constants::match_not_bol
- regex/std::regex_constants::match_not_eol
- regex/std::regex_constants::match_not_bow
- regex/std::regex_constants::match_not_eow
- regex/std::regex_constants::match_any
- regex/std::regex_constants::match_not_null
- regex/std::regex_constants::match_continuous
- regex/std::regex_constants::match_prev_avail
- regex/std::regex_constants::format_default
- regex/std::regex_constants::format_sed
- regex/std::regex_constants::format_no_copy
- regex/std::regex_constants::format_first_only
- regex/std::regex_constants::ECMAScript
- regex/std::regex_constants::basic
- regex/std::regex_constants::extended
- regex/std::regex_constants::awk
- regex/std::regex_constants::grep
- regex/std::regex_constants::egrep
- regex/std::regex_constants::icase
- regex/std::regex_constants::nosubs
- regex/std::regex_constants::optimize
- regex/std::regex_constants::collate
helpviewer_keywords:
- std::regex_constants [C++]
- std::regex_constants [C++], error_collate
- std::regex_constants [C++], error_ctype
- std::regex_constants [C++], error_escape
- std::regex_constants [C++], error_backref
- std::regex_constants [C++], error_brack
- std::regex_constants [C++], error_paren
- std::regex_constants [C++], error_brace
- std::regex_constants [C++], error_badbrace
- std::regex_constants [C++], error_range
- std::regex_constants [C++], error_space
- std::regex_constants [C++], error_badrepeat
- std::regex_constants [C++], error_complexity
- std::regex_constants [C++], error_stack
- std::regex_constants [C++], error_parse
- std::regex_constants [C++], error_syntax
- std::regex_constants [C++], match_default
- std::regex_constants [C++], match_not_bol
- std::regex_constants [C++], match_not_eol
- std::regex_constants [C++], match_not_bow
- std::regex_constants [C++], match_not_eow
- std::regex_constants [C++], match_any
- std::regex_constants [C++], match_not_null
- std::regex_constants [C++], match_continuous
- std::regex_constants [C++], match_prev_avail
- std::regex_constants [C++], format_default
- std::regex_constants [C++], format_sed
- std::regex_constants [C++], format_no_copy
- std::regex_constants [C++], format_first_only
- std::regex_constants [C++], ECMAScript
- std::regex_constants [C++], basic
- std::regex_constants [C++], extended
- std::regex_constants [C++], awk
- std::regex_constants [C++], grep
- std::regex_constants [C++], egrep
- std::regex_constants [C++], icase
- std::regex_constants [C++], nosubs
- std::regex_constants [C++], optimize
- std::regex_constants [C++], collate
ms.assetid: 4a69c0ba-c46d-46e4-bd29-6f4efb805f26
ms.openlocfilehash: c8abca8109db9c781d63721b795feb01161fdb40
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451669"
---
# <a name="regexconstants-namespace"></a>regex_constants 命名空间

正则表达式标志的命名空间。

## <a name="syntax"></a>语法

```cpp
namespace regex_constants {
    enum syntax_option_type;
    enum match_flag_type;
    enum error_type;
}
```

## <a name="remarks"></a>备注

命名空间 `regex_constants` 封装若干标记类型及其关联的标记值。

|||
|-|-|
|[error_type](#error_type)|用于报告正则表达式语法错误的标志。|
|[match_flag_type](#match_flag_type)|正则表达式匹配选项的标志。|
|[syntax_option_type](#syntax_option_type)|用于选择语法选项的标志。|

## <a name="requirements"></a>要求

**标头：** \<regex 1>

**命名空间：** std

## <a name="error_type"></a>regex_constants::error_type

用于报告正则表达式语法错误的标志。

```cpp
enum error_type
    {    // identify error
    error_collate,
    error_ctype,
    error_escape,
    error_backref,
    error_brack,
    error_paren,
    error_brace,
    error_badbrace,
    error_range,
    error_space,
    error_badrepeat,
    error_complexity,
    error_stack,
    error_parse,
    error_syntax
    };
```

### <a name="remarks"></a>备注

该类型是一个枚举类型，它描述可保留错误标志的对象。 非重复的标志值为：

`error_backref` - 表达式中包含无效的向后引用

`error_badbrace` - 表达式在 { } 表达式中包含无效计数

`error_badrepeat` - 重复表达式（在大多数上下文中为“*”、“?”、“+”、“{”之一）后没有表达式

`error_brace` - 表达式中包含不匹配的“'{”或“}”

`error_brack` - 表达式中包含不匹配的“[”或“]”

`error_collate` - 表达式中包含无效的排序规则元素名

`error_complexity` - 尝试匹配失败，因为它太复杂

`error_ctype` - 表达式中包含无效的字符类名

`error_escape` - 表达式包含无效转义序列

`error_paren` - 表达式中包含不匹配的“(”或“)”

`error_parse` - 表达式解析失败

`error_range` - 表达式中包含无效的字符范围说明符

`error_space` - 分析正则表达式失败，因为没有足够的资源

`error_stack` - 所尝试匹配失败，因为没有足够的内存

`error_syntax` - 分析因语法错误失败

`error_backref` - 表达式中包含无效的向后引用

## <a name="match_flag_type"></a>  regex_constants::match_flag_type

正则表达式匹配选项的标志。

```cpp
enum match_flag_type
    {    // specify matching and formatting rules
    match_default = 0x0000,
    match_not_bol = 0x0001,
    match_not_eol = 0x0002,
    match_not_bow = 0x0004,
    match_not_eow = 0x0008,
    match_any = 0x0010,
    match_not_null = 0x0020,
    match_continuous = 0x0040,
    match_prev_avail = 0x0100,
    format_default = 0x0000,
    format_sed = 0x0400,
    format_no_copy = 0x0800,
    format_first_only = 0x1000,
    _Match_not_null = 0x2000
    };
```

### <a name="remarks"></a>备注

该类型是位掩码类型，用于描述针对替换文本时使用的正则表达式和格式标志匹配文本序列时使用的选项。 可与 `|`组合使用的选项。

匹配选项包括：

`match_default`

`match_not_bol` - 不将目标序列中的第一个位置视为行首

`match_not_eol` - 不将目标序列中超过末尾的位置视为行尾

`match_not_bow` - 不将目标序列中的第一个位置视为单词的开头

`match_not_eow` - 不将目标序列中超过末尾的位置视为单词的结尾

`match_any` - 如果有多个匹配，任何匹配都是可接受的

`match_not_null` - 不要将空的子序列视为匹配项

`match_continuous` - 不搜索除目标序列开头位置之外的匹配项

`match_prev_avail` --  是有效的迭代器，请忽略 `--first``match_not_bol` 和 `match_not_bow`（如果已设置）

格式标志包括：

`format_default` -- 使用 ECMAScript 格式规则

`format_sed` -- 使用 sed 格式规则

`format_no_copy` -- 不复制与正则表达式不匹配的文本

`format_first_only` - 不搜索第一个匹配项之后的匹配项

## <a name="syntax_option_type"></a>  regex_constants::syntax_option_type

用于选择语法选项的标志。

```cpp
enum syntax_option_type
    {    // specify RE syntax rules
    ECMAScript = 0x01,
    basic = 0x02,
    extended = 0x04,
    awk = 0x08,
    grep = 0x10,
    egrep = 0x20,
    _Gmask = 0x3F,

    icase = 0x0100,
    nosubs = 0x0200,
    optimize = 0x0400,
    collate = 0x0800
    };
```

### <a name="remarks"></a>备注

该类型为位掩码类型，用于描述编译正则表达式时要使用的语言说明符和语法修饰符。 可与 `|`组合使用的选项。 一次不能使用多于一个语言说明符。

语言说明符有：

`ECMAScript` -- 编译为 ECMAScript

`basic` -- 编译为 BRE

`extended` -- 编译为 ERE

`awk` -- 编译为 awk

`grep` -- 编译为 grep

`egrep` -- 编译为 egrep

语法修饰符有：

`icase` -- 匹配不区分大小写

`nosubs` -- 实现不需要跟踪捕获组的内容

`optimize` -- 实现应强调匹配的速度而非正则表达式编译的速度

`collate` -- 进行区分区域设置的匹配

## <a name="see-also"></a>请参阅

[\<regex>](../standard-library/regex.md)\
[regex_error 类](../standard-library/regex-error-class.md)\
[\<regex > 函数](../standard-library/regex-functions.md)\
[regex_iterator 类](../standard-library/regex-iterator-class.md)\
[\<regex > 运算符](../standard-library/regex-operators.md)\
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)\
[regex_traits 类](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
