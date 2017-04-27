---
title: "regex_constants 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex_constants
- regex/std::regex_constants
- error_collate
- regex/std::regex_constants::error_collate
- error_ctype
- regex/std::regex_constants::error_ctype
- error_escape
- regex/std::regex_constants::error_escape
- error_backref
- regex/std::regex_constants::error_backref
- error_brack
- regex/std::regex_constants::error_brack
- error_paren
- regex/std::regex_constants::error_paren
- error_brace
- regex/std::regex_constants::error_brace
- error_badbrace
- regex/std::regex_constants::error_badbrace
- error_range
- regex/std::regex_constants::error_range
- error_space
- regex/std::regex_constants::error_space
- error_badrepeat
- regex/std::regex_constants::error_badrepeat
- error_complexity
- regex/std::regex_constants::error_complexity
- error_stack
- regex/std::regex_constants::error_stack
- error_parse
- regex/std::regex_constants::error_parse
- error_syntax
- regex/std::regex_constants::error_syntax
- match_default
- regex/std::regex_constants::match_default
- match_not_bol
- regex/std::regex_constants::match_not_bol
- match_not_eol
- regex/std::regex_constants::match_not_eol
- match_not_bow
- regex/std::regex_constants::match_not_bow
- match_not_eow
- regex/std::regex_constants::match_not_eow
- match_any
- regex/std::regex_constants::match_any
- match_not_null
- regex/std::regex_constants::match_not_null
- match_continuous
- regex/std::regex_constants::match_continuous
- match_prev_avail
- regex/std::regex_constants::match_prev_avail
- format_default
- regex/std::regex_constants::format_default
- format_sed
- regex/std::regex_constants::format_sed
- format_no_copy
- regex/std::regex_constants::format_no_copy
- format_first_only
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
dev_langs:
- C++
helpviewer_keywords:
- regex_constants class
ms.assetid: 4a69c0ba-c46d-46e4-bd29-6f4efb805f26
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 248e9ba676b906af62f6804f4939e04158a8e2ef
ms.openlocfilehash: 9330a5c4e1b487880f405478dd7e8838af739c44
ms.lasthandoff: 02/24/2017

---
# <a name="regexconstants-class"></a>regex_constants 类
正则表达式标志的命名空间。  
  
## <a name="syntax"></a>语法  
  
```  
namespace regex_constants {  
    enum syntax_option_type;  
    enum match_flag_type;  
    enum error_type;  
 }  
```  
  
## <a name="remarks"></a>备注  
 命名空间 `regex_constants` 封装若干标记类型及其关联的标记值。  
  
## <a name="requirements"></a>要求  
 **标头：**\<regex&1;>  
  
 **命名空间：** std  
  
##  <a name="regex_constants__error_type"></a>regex_constants::error_type  
 用于报告正则表达式语法错误的标志。  
  
```  
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
  
##  <a name="regex_constants__match_flag_type"></a>  regex_constants::match_flag_type  
 正则表达式匹配选项的标志。  
  
```  
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
  
##  <a name="regex_constants__syntax_option_type"></a>  regex_constants::syntax_option_type  
 用于选择语法选项的标志。  
  
```  
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
  
## <a name="see-also"></a>另请参阅  
[\<regex>](../standard-library/regex.md)  
[regex_error 类](../standard-library/regex-error-class.md)  
[\<regex> functions](../standard-library/regex-functions.md)  
[regex_iterator 类](../standard-library/regex-iterator-class.md)  
[\<regex> operators](../standard-library/regex-operators.md)  
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)  
[regex_traits 类](../standard-library/regex-traits-class.md)  
[\<regex> typedefs](../standard-library/regex-typedefs.md)  

