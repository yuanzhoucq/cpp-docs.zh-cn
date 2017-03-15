---
title: "&lt;locale&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<locale>"
  - "std.<locale>"
  - "locale/std::<locale>"
  - "std::<locale>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "locale 标头"
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt;locale&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义模板类和函数，以便 C\+\+ 程序用来封装和操作与数字、货币和日历数据的表示及格式化有关的不同区域性约定，包括字符分类和字符串排序规则的国际化支持。  
  
## 语法  
  
```  
  
#include <locale>  
  
```  
  
### Functions  
  
|||  
|-|-|  
|[has\_facet](../Topic/has_facet.md)|测试某一特定 facet 是否存储在指定区域设置中。|  
|[isalnum](../Topic/isalnum.md)|测试区域设置中的某一元素是否是字母字符或数字字符。|  
|[isalpha](../Topic/isalpha.md)|测试区域设置中的某一元素是否是字母字符。|  
|[iscntrl](../Topic/iscntrl.md)|测试区域设置中的某一元素是否是控制字符。|  
|[isdigit](../Topic/isdigit.md)|测试区域设置中的某一元素是否是数字字符。|  
|[isgraph](../Topic/isgraph.md)|测试区域设置中的某一元素是否是字母数字字符或标点字符。|  
|[islower](../Topic/islower.md)|测试区域设置中的某一元素是否是小写。|  
|[isprint](../Topic/isprint.md)|测试区域设置中的某一元素是否是可打印字符。|  
|[ispunct](../Topic/ispunct.md)|测试区域设置中的某一元素是否是标点字符。|  
|[isspace](../Topic/isspace.md)|测试区域设置中的某一元素是否是空白字符。|  
|[isupper](../Topic/isupper.md)|测试区域设置中的某一元素是否是大写。|  
|[isxdigit](../Topic/isxdigit.md)|测试区域设置中的某一元素是否是用于表示十六进制数字的字符。|  
|[tolower](../Topic/tolower.md)|将字符转换为小写。|  
|[toupper](../Topic/toupper.md)|将字符转换为大写。|  
|[use\_facet](../Topic/use_facet.md)|返回对区域设置中存储的某一指定类型 facet 的引用。|  
  
### 类  
  
|||  
|-|-|  
|[codecvt](../standard-library/codecvt-class.md)|提供一种 facet 的模板类，可使用此 facet 在内部和外部字符编码之间进行转换。|  
|[codecvt\_base](../standard-library/codecvt-base-class.md)|一种 codecvt 类的基类，用于定义一种称为 **result** 的枚举类型，此类型用作 facet 成员函数的返回类型以便指示转换结果。|  
|[codecvt\_byname](../standard-library/codecvt-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的排序规则 facet，从而检索与转换有关的文化区域特定信息。|  
|[collate](../standard-library/collate-class.md)|一种排序规则模板类，用于提供一个 facet 来处理字符串排序约定。|  
|[collate\_byname](../standard-library/collate-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的排序规则 facet，从而检索与字符串排序约定有关的文化区域特定信息。|  
|[ctype](../standard-library/ctype-class.md)|一种模板类，可提供一个 facet，用于对字符进行分类、转换大写和小写以及在本机字符集与区域设置使用的字符集之间进行转换。|  
|[ctype\<char\>](../standard-library/ctype-char-class.md)|一个将模板类 **ctype\<CharType**\> 显式专用化到类型 `char` 的类，它描述一个可充当区域设置 facet 的对象，用来表示类型 `char` 的字符的各种属性特征。|  
|[ctype\_base](../standard-library/ctype-base-class.md)|一种 ctype 类的基类，用于定义枚举类型来分类或测试单个字符或整个范围内的字符。|  
|[ctype\_byname](../standard-library/ctype-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的 ctype facet，从而对字符进行分类，并在大小写之间以及本机字符集和区域设置指定字符集之间进行转换。|  
|[Locale — 区域设置](../standard-library/locale-class.md)|一种描述区域设置对象的类，可将区域性特定信息封装为一组 facet，以便共同定义特定的本地化环境。|  
|[消息](../standard-library/messages-class.md)|一种模板类，用于描述一个对象来充当区域设置 facet，以便从给定区域设置的国际化消息目录中检索本地化消息。|  
|[messages\_base](../standard-library/messages-base-class.md)|一种基类，用于描述消息目录的 `int` 类型。|  
|[messages\_byname](../standard-library/messages-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的信息 facet，从而检索本地化消息。|  
|[money\_base](../standard-library/money-base-class.md)|一种 ctype 类的基类，用于定义枚举类型来分类或测试单个字符或整个范围内的字符。|  
|[money\_get](../standard-library/money-get-class.md)|一种模板类，用于描述一个对象来充当区域设置 facet，以便控制 **CharType** 类型的序列向货币值的转换。|  
|[money\_put](../standard-library/money-put-class.md)|一种模板类，用于描述一个对象来充当区域设置 facet，以便控制货币值向 **CharType** 类型的序列的转换。|  
|[moneypunct](../standard-library/moneypunct-class.md)|一种模板类，用于描述一个对象来充当区域设置 facet，以便描述用来表示货币输入字段或货币输出字段的 **CharType** 类序列。|  
|[moneypunct\_byname](../standard-library/moneypunct-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的 moneypunct facet，从而对货币输入或输出字段进行格式化。|  
|[num\_get](../standard-library/num-get-class.md)|一种模板类，用于描述一个对象来充当区域设置 facet，以便控制 **CharType** 类型的序列向数值的转换。|  
|[num\_put](../standard-library/num-put-class.md)|一种模板类，用于描述一个对象来充当区域设置 facet，以便控制数值向 **CharType** 类序列的转换。|  
|[numpunct](../standard-library/numpunct-class.md)|一种模板类，用于描述一个对象来充当区域设置 facet，以便描述 **CharType** 类型的序列，后者用于表示与数字和布尔表达式的格式化及标点有关的信息。|  
|[numpunct\_byname](../standard-library/numpunct-byname-class.md)|一种派生模板类，用于描述一个对象来充当给定区域设置的 moneypunct facet，从而数字和布尔表达式进行格式化和标点设置。|  
|[time\_base](../standard-library/time-base-class.md)|一种充当模板类 time\_get 的 facet 基类的类，用于仅定义枚举的类型 dateorder 以及此类型的几个常量。|  
|[time\_get](../standard-library/time-get-class.md)|一种模板类，用于描述一个对象来充当区域设置 facet，以便控制 **CharType** 类型的序列向时间值的转换。|  
|[time\_get\_byname](../standard-library/time-get-byname-class.md)|一种派生模板类，用于描述一个可充当类型 time\_get\<**CharType**、**InputIterator**\> 的区域设置 facet 的对象。|  
|[time\_put](../standard-library/time-put-class.md)|一种模板类，用于描述一个对象来充当区域设置 facet，以便控制时间值向 **CharType** 类序列的转换。|  
|[time\_put\_byname](../standard-library/time-put-byname-class.md)|一种派生模板类，用于描述一个可充当类型 `time_put`\<**CharType**、**OutputIterator**\> 的区域设置 facet 的对象。|  
|[wbuffer\_convert 类](../standard-library/wbuffer-convert-class.md)|描述用于控制元素与字节流缓冲区之间的来回传输的流缓冲区。|  
|[wstring\_convert 类](../standard-library/wstring-convert-class.md)|一种在宽字符串和字节字符串之间执行转换的模板类。|  
  
## 请参阅  
 [代码页](../c-runtime-library/code-pages.md)   
 [区域设置名称、语言和国家\/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)