---
title: '&lt;string&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- string/std::<string>
- <string>
dev_langs: C++
helpviewer_keywords: string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 14442f2de89c055b35614951a277366616e00250
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ltstringgt"></a>&lt;字符串&gt;
定义容器模板类 `basic_string` 和各种支持模板。  
  
 有关 `basic_string` 的详细信息，请参阅[basic_string Class](../standard-library/basic-string-class.md)  
  
## <a name="syntax"></a>语法  
  
```  
#include <string>  
```  
  
## <a name="remarks"></a>备注  
 C++ 语言和 C++ 标准库支持两种类型的字符串：  
  
-   以 null 结尾的字符数组通常作为 C 字符串被引用。  
  
-   属于类 `basic_string` 的模板类对象，它处理类似于 `char` 的所有模板参数。  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[字符串](../standard-library/string-typedefs.md#string)|使用 `basic_string` 类型的元素将 `char` 模板类的专用化描述为 `string` 的类型。|  
|[wstring](../standard-library/string-typedefs.md#wstring)|使用 `basic_string` 类型的元素将 `wchar_t` 模板类的专用化描述为 `wstring` 的类型。|  
|[u16string](../standard-library/string-typedefs.md#u16string)|基于 `basic_string` 类型的元素描述模板类 `char16_t` 的专用化的类型。|  
|[u32string](../standard-library/string-typedefs.md#u32string)|基于 `basic_string` 类型的元素描述模板类 `char32_t` 的专用化的类型。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator+](../standard-library/string-operators.md#op_add)|连接两个字符串对象。|  
|[operator!=](../standard-library/string-operators.md#op_neq)|测试运算符左侧的字符串对象是否不等于右侧的字符串对象。|  
|[operator==](../standard-library/string-operators.md#op_eq_eq)|测试运算符左侧的字符串对象是否等于右侧的字符串对象。|  
|[operator<](../standard-library/string-operators.md#op_lt)|测试运算符左侧的字符串对象是否小于右侧的字符串对象。|  
|[operator<=](../standard-library/string-operators.md#op_lt_eq)|测试运算符左侧的字符串对象是否小于或等于右侧的字符串对象。|  
|[operator<\<](../standard-library/string-operators.md#op_lt_lt)|一个模板函数，用于向输出流插入字符串。|  
|[operator>](../standard-library/string-operators.md#op_gt)|测试运算符左侧的字符串对象是否大于右侧的字符串对象。|  
|[operator>=](../standard-library/string-operators.md#op_gt_eq)|测试运算符左侧的字符串对象是否大于或等于右侧的字符串对象。|  
|[operator>>](../standard-library/string-operators.md#op_gt_gt)|一个模板函数，用于从输入流提取字符串。|  
  
### <a name="specialized-template-functions"></a>专用化模板函数  
  
|||  
|-|-|  
|[swap](../standard-library/string-functions.md#swap)|交换两个字符串的字符数组。|  
|[stod](../standard-library/string-functions.md#stod)|将字符序列转换为 `double.`|  
|[stof](../standard-library/string-functions.md#stof)|将字符序列转换为 `float`。|  
|[stoi](../standard-library/string-functions.md#stoi)|将字符序列转换为整数。|  
|[stold](../standard-library/string-functions.md#stold)|将字符序列转换为 `long double`。|  
|[stoll](../standard-library/string-functions.md#stoll)|将字符序列转换为 `long long`。|  
|[stoul](../standard-library/string-functions.md#stoul)|将字符序列转换为 `unsigned long`。|  
|[stoull](../standard-library/string-functions.md#stoull)|将字符序列转换为 `unsigned long long`。|  
|[to_string](../standard-library/string-functions.md#to_string)|将一个值转换为 `string`。|  
|[to_wstring](../standard-library/string-functions.md#to_wstring)|将一个值转换为宽 `string`。|  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[getline 模板](../standard-library/string-functions.md#getline)|将字符串从输入流中一行一行地提取出来。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[basic_string 类](../standard-library/basic-string-class.md)|一个模板类，用于描述可存储任意字符类对象序列的对象。|  
|[char_traits 结构](../standard-library/char-traits-struct.md)|一个模板类，用于描述与类型 CharType 的字符关联的特性。|  
  
### <a name="specializations"></a>专用化  
  
|||  
|-|-|  
|[char_traits\<char> Struct](../standard-library/char-traits-char-struct.md)|一个结构，它是模板结构 `char_traits`\<CharType> 对类型 `char` 元素的专用化。|  
|[char_traits<wchar_t> 结构](../standard-library/char-traits-wchar-t-struct.md)|一个结构，它是模板结构 `char_traits`\<CharType> 对类型 `wchar_t` 元素的专用化。|  
|[char_traits<char16_t> 结构](../standard-library/char-traits-char16-t-struct.md)|一个结构，它是模板结构 `char_traits`\<CharType> 对类型 `char16_t` 元素的专用化。|  
|[char_traits<char32_t> 结构](../standard-library/char-traits-char32-t-struct.md)|一个结构，它是模板结构 `char_traits`\<CharType> 对类型 `char32_t` 元素的专用化。|  
  
## <a name="requirements"></a>惠?  
  
- **标头：** \<string>  
  
- **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



