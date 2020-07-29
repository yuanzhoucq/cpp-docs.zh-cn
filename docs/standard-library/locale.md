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
ms.openlocfilehash: ae008ef45e8a6bb57505432f2c931a768d4c8ea4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224794"
---
# <a name="ltlocalegt"></a>&lt;locale&gt;

定义类模板和函数，c + + 程序可以使用这些模板和函数来封装和操作有关数字、货币和日历数据的表示形式和格式的不同区域性约定，包括对字符分类和字符串排序规则的国际化支持。

## <a name="syntax"></a>语法

```cpp
#include <locale>
```

### <a name="functions"></a>函数

|函数|说明|
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

|类|说明|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|提供用于在内部和外部字符编码之间进行转换的 facet 的类模板。|
|[codecvt_base](../standard-library/codecvt-base-class.md)|用于定义称为的枚举类型的 codecvt 类的基类 `result` ，用作 facet 成员函数的返回类型，以指示转换的结果。|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|一个派生类模板，用于描述一个对象，该对象可充当给定区域设置的排序规则 facet，从而能够检索涉及转换的文化区域的信息。|
|[collate](../standard-library/collate-class.md)|一种排序类模板，用于提供处理字符串排序约定的方面。|
|[collate_byname](../standard-library/collate-byname-class.md)|一个派生类模板，用于描述一个对象，该对象可充当给定区域设置的排序规则 facet，从而能够检索特定于涉及字符串排序约定的区域性区域的信息。|
|[ctype](../standard-library/ctype-class.md)|一个类模板，该模板提供用于对字符进行分类、在本机字符集和本地字符集之间进行转换的方面以及区域设置使用的设置。|
|[ctype\<char>](../standard-library/ctype-char-class.md)|一个类，该类是类模板的显式专用化 `ctype<CharType>` 到类型 **`char`** ，它描述可用作区域设置 facet 的对象，以便为类型的字符的各种属性设置特征 **`char`** 。|
|[ctype_base](../standard-library/ctype-base-class.md)|一种 ctype 类的基类，用于定义枚举类型来分类或测试单个字符或整个范围内的字符。|
|[ctype_byname](../standard-library/ctype-byname-class.md)|一种派生类模板，用于描述一个对象，该对象可充当给定区域设置的 ctype facet，启用字符分类以及区分大小写和本地和区域设置指定字符集之间的字符的转换。|
|[locale](../standard-library/locale-class.md)|一种描述区域设置对象的类，可将区域性特定信息封装为一组 facet，以便共同定义特定的本地化环境。|
|[messages](../standard-library/messages-class.md)|一个类模板，用于描述一个对象，该对象可充当区域设置 facet，以便从给定区域设置的国际化消息目录中检索本地化消息。|
|[messages_base](../standard-library/messages-base-class.md)|描述 **`int`** 消息目录的类型的基类。|
|[messages_byname](../standard-library/messages-byname-class.md)|一种派生类模板，用于描述一个对象，该对象可充当给定区域设置的消息方面，并支持检索本地化消息。|
|[money_base](../standard-library/money-base-class.md)|一种 ctype 类的基类，用于定义枚举类型来分类或测试单个字符或整个范围内的字符。|
|[money_get](../standard-library/money-get-class.md)|一个类模板，用于描述一个对象，该对象可充当区域设置 facet，以便控制**CharType**类型的序列到货币值的转换。|
|[money_put](../standard-library/money-put-class.md)|一个类模板，用于描述一个对象，该对象可充当区域设置 facet，以便控制货币值到**CharType**类型的转换。|
|[moneypunct](../standard-library/moneypunct-class.md)|一个类模板，该模板描述可用作区域设置 facet 的对象，以描述用于表示货币输入字段或货币输出字段的**CharType**类型的序列。|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|一个派生类模板，用于描述一个对象，该对象可充当给定区域设置的 moneypunct facet，从而启用格式货币输入或输出字段。|
|[num_get](../standard-library/num-get-class.md)|一个类模板，用于描述一个对象，该对象可充当区域设置 facet，以便控制**CharType**类型的序列到数值的转换。|
|[num_put](../standard-library/num-put-class.md)|一个类模板，用于描述一个对象，该对象可充当区域设置 facet，以便控制数值到类型**CharType**的序列的转换。|
|[numpunct](../standard-library/numpunct-class.md)|一个类模板，用于描述一个对象，该对象可用作本地方面，以描述用于表示有关数值和布尔表达式的格式和标点的信息的**CharType**类型的序列。|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|一个派生类模板，用于描述一个对象，该对象可充当给定区域设置的 moneypunct facet，从而支持数值和布尔表达式的格式设置和标点。|
|[time_base](../standard-library/time-base-class.md)|一个类，该类用作类模板 time_get 的各个方面的基类，只定义枚举的类型 dateorder 和此类型的几个常量。|
|[time_get](../standard-library/time-get-class.md)|一个类模板，用于描述一个对象，该对象可充当区域设置 facet，以控制**CharType**类型的序列到时间值的转换。|
|[time_get_byname](../standard-library/time-get-byname-class.md)|一个派生类模板，用于描述一个对象，该对象可充当类型 time_get 的区域设置 facet \<**CharType**, **InputIterator**> 。|
|[time_put](../standard-library/time-put-class.md)|一个类模板，用于描述一个对象，该对象可充当区域设置 facet，以控制将时间值转换为**CharType**类型的序列。|
|[time_put_byname](../standard-library/time-put-byname-class.md)|一个派生类模板，用于描述一个可充当类型的区域设置 facet 的对象 `time_put` \<**CharType**, **OutputIterator**> 。|
|[wbuffer_convert 类](../standard-library/wbuffer-convert-class.md)|描述用于控制元素与字节流缓冲区之间的来回传输的流缓冲区。|
|[wstring_convert 类](../standard-library/wstring-convert-class.md)|一个类模板，它在宽字符串和字节字符串之间执行转换。|

## <a name="see-also"></a>另请参阅

[代码页](../c-runtime-library/code-pages.md)\
[区域设置名称、语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
