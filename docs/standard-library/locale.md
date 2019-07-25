---
title: '&lt;locale&gt;'
ms.date: 11/04/2016
f1_keywords:
- <locale>
- locale/std::<locale>
- std::<locale>
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
ms.openlocfilehash: 708184a6a6a443456f0d70f57b6be17b281ac4f5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453918"
---
# <a name="ltlocalegt"></a>&lt;locale&gt;

定义模板类和函数，以便 C++ 程序用来封装和操作与数字、货币和日历数据的表示及格式化有关的不同区域性约定，包括字符分类和字符串排序规则的国际化支持。

## <a name="syntax"></a>语法

```cpp
#include <locale>
```

### <a name="functions"></a>函数

|函数|描述|
|-|-|
|[has_facet](../standard-library/locale-functions.md#has_facet)|测试某一特定 facet 是否存储在指定区域设置中。|
|[isalnum](../standard-library/locale-functions.md#isalnum)|测试区域设置中的某一元素是否是字母字符或数字字符。|
|[isalpha](../standard-library/locale-functions.md#isalpha)|测试区域设置中的某一元素是否是字母字符。|
|[iscntrl](../standard-library/locale-functions.md#iscntrl)|测试区域设置中的某一元素是否是控制字符。|
|[isdigit](../standard-library/locale-functions.md#isdigit)|测试区域设置中的某一元素是否是数字字符。|
|[isgraph](../standard-library/locale-functions.md#isgraph)|测试区域设置中的某一元素是否是字母数字字符或标点字符。|
|[islower](../standard-library/locale-functions.md#islower)|测试区域设置中的某一元素是否是小写。|
|[isprint](../standard-library/locale-functions.md#isprint)|测试区域设置中的某一元素是否是可打印字符。|
|[ispunct](../standard-library/locale-functions.md#ispunct)|测试区域设置中的某一元素是否是标点字符。|
|[isspace](../standard-library/locale-functions.md#isspace)|测试区域设置中的某一元素是否是空白字符。|
|[isupper](../standard-library/locale-functions.md#isupper)|测试区域设置中的某一元素是否是大写。|
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|测试区域设置中的某一元素是否是用于表示十六进制数字的字符。|
|[tolower](../standard-library/locale-functions.md#tolower)|将字符转换为小写。|
|[toupper](../standard-library/locale-functions.md#toupper)|将字符转换为大写。|
|[use_facet](../standard-library/locale-functions.md#use_facet)|返回对区域设置中存储的某一指定类型 facet 的引用。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|提供一种 facet 的模板类，可使用此 facet 在内部和外部字符编码之间进行转换。|
|[codecvt_base](../standard-library/codecvt-base-class.md)|用于定义称为`result`的枚举类型的 codecvt 类的基类, 用作 facet 成员函数的返回类型, 以指示转换的结果。|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的排序规则 facet，从而检索与转换有关的文化区域特定信息。|
|[collate](../standard-library/collate-class.md)|一种排序规则模板类，用于提供一个 facet 来处理字符串排序约定。|
|[collate_byname](../standard-library/collate-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的排序规则 facet，从而检索与字符串排序约定有关的文化区域特定信息。|
|[ctype](../standard-library/ctype-class.md)|一种模板类，可提供一个 facet，用于对字符进行分类、转换大写和小写以及在本机字符集与区域设置使用的字符集之间进行转换。|
|[ctype\<char>](../standard-library/ctype-char-class.md)|作为模板类`ctype<CharType>`的显式专用化到类型**char**的类, 描述可用作区域设置 facet 的对象, 以描述类型为**char**的字符的各种属性。|
|[ctype_base](../standard-library/ctype-base-class.md)|一种 ctype 类的基类，用于定义枚举类型来分类或测试单个字符或整个范围内的字符。|
|[ctype_byname](../standard-library/ctype-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的 ctype facet，从而对字符进行分类，并在大小写之间以及本机字符集和区域设置指定字符集之间进行转换。|
|[locale](../standard-library/locale-class.md)|一种描述区域设置对象的类，可将区域性特定信息封装为一组 facet，以便共同定义特定的本地化环境。|
|[messages](../standard-library/messages-class.md)|一种模板类，用于描述一个对象来充当区域设置 facet，以便从给定区域设置的国际化消息目录中检索本地化消息。|
|[messages_base](../standard-library/messages-base-class.md)|描述消息目录的**int**类型的基类。|
|[messages_byname](../standard-library/messages-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的信息 facet，从而检索本地化消息。|
|[money_base](../standard-library/money-base-class.md)|一种 ctype 类的基类，用于定义枚举类型来分类或测试单个字符或整个范围内的字符。|
|[money_get](../standard-library/money-get-class.md)|一个模板类, 用于描述可用作区域设置 facet 的对象, 以控制**CharType**类型的序列到货币值的转换。|
|[money_put](../standard-library/money-put-class.md)|一个模板类, 用于描述可用作区域设置 facet 的对象, 以便控制货币值到**CharType**类型的转换。|
|[moneypunct](../standard-library/moneypunct-class.md)|一个模板类, 用于描述可用作区域设置 facet 的对象, 用于描述用于表示货币输入字段或货币输出字段的**CharType**类型的序列。|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的 moneypunct facet，从而对货币输入或输出字段进行格式化。|
|[num_get](../standard-library/num-get-class.md)|一个模板类, 用于描述可用作区域设置 facet 的对象, 以控制**CharType**类型的序列到数值的转换。|
|[num_put](../standard-library/num-put-class.md)|一个模板类, 用于描述可用作区域设置 facet 的对象, 以控制数值到类型**CharType**的序列的转换。|
|[numpunct](../standard-library/numpunct-class.md)|一个模板类, 用于描述一个对象, 该对象可用作本地方面, 以描述用于表示有关数值和布尔表达式的格式和标点的信息的**CharType**类型的序列。|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的 moneypunct facet，从而数字和布尔表达式进行格式化和标点设置。|
|[time_base](../standard-library/time-base-class.md)|一种充当模板类 time_get 的 facet 基类的类，用于仅定义枚举的类型 dateorder 以及此类型的几个常量。|
|[time_get](../standard-library/time-get-class.md)|一个模板类, 用于描述可用作区域设置 facet 的对象, 以控制**CharType**类型的序列到时间值的转换。|
|[time_get_byname](../standard-library/time-get-byname-class.md)|一种派生模板类, 用于描述可用作 time_get\<**CharType**, **InputIterator**> 类型的区域设置 facet 的对象。|
|[time_put](../standard-library/time-put-class.md)|一个模板类, 用于描述可用作区域设置 facet 的对象, 以控制将时间值转换为**CharType**类型的序列。|
|[time_put_byname](../standard-library/time-put-byname-class.md)|一种派生模板类, 用于`time_put`描述可用作类型\<为**CharType**、 **OutputIterator**> 的区域设置 facet 的对象。|
|[wbuffer_convert 类](../standard-library/wbuffer-convert-class.md)|描述用于控制元素与字节流缓冲区之间的来回传输的流缓冲区。|
|[wstring_convert 类](../standard-library/wstring-convert-class.md)|一种在宽字符串和字节字符串之间执行转换的模板类。|

## <a name="see-also"></a>请参阅

[代码页](../c-runtime-library/code-pages.md)\
[区域设置名称、语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
