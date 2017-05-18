---
title: "wstring_convert 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- wstring_convert
- stdext::cvt::wstring_convert
- cvt::wstring_convert
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
dev_langs:
- C++
helpviewer_keywords:
- wstring_convert class
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 9545a1c559574bd5dc86e8924a65db9bea8cf9ae
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="wstringconvert-class"></a>wstring_convert 类
模板类 `wstring_convert` 在宽字符串和字节字符串之间执行转换。  
  
## <a name="syntax"></a>语法  
  
```
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```  
  
#### <a name="parameters"></a>参数  
 Codecvt  
 表示转换对象的[区域设置](../standard-library/locale-class.md)方面。  
  
 Elem  
 宽字符元素类型。  
  
## <a name="remarks"></a>备注  
 模板类描述一个对象，该对象用于控制类 `std::basic_string<Elem>` 的宽字符串对象和类 `std::basic_string<char>`（也称为 `std::string`）的字节字符串对象之间的转换。 模板类将类型 `wide_string` 和 `byte_string` 定义为这两种类型的同义词。 一个 `Elem` 值序列（存储在 `wide_string` 对象中）和多字节序列（存储在 `byte_string` 对象中）之间的转换由类 `Codecvt<Elem, char, std::mbstate_t>` 的对象执行，这符合标准代码转换方面 `std::codecvt<Elem, char, std::mbstate_t>` 的要求。  
  
 此模板类的对象存储：  
  
-   发生错误时显示的字节字符串  
  
-   发生错误时显示的宽字符串  
  
-   指向分配的转换对象（在销毁 wbuffer_convert 对象时释放）的指针  
  
-   [state_type](#state_type) 类型的转换状态对象  
  
-   转换计数  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[wstring_convert](#wstring_convert)|构造 `wstring_convert` 类型的对象。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[byte_string](#byte_string)|表示字节字符串的类型。|  
|[wide_string](#wide_string)|表示宽字符串的类型。|  
|[state_type](#state_type)|表示转换状态的类型。|  
|[int_type](#int_type)|表示整数的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[from_bytes](#from_bytes)|将字节字符串转换为宽字符串。|  
|[to_bytes](#to_bytes)|将宽字符串转换为字节字符串。|  
|[converted](#converted)|返回成功转换数。|  
|[state](#state)|返回表示转换状态的对象。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
##  <a name="byte_string"></a>wstring_convert::byte_string  
 表示字节字符串的类型。  
  
```
typedef std::basic_string<char> byte_string;
```  
  
### <a name="remarks"></a>备注  
 该类型是 `std::basic_string<char>` 的同义词。  
  
##  <a name="converted"></a>wstring_convert::converted  
 返回成功转换数。  
  
```
size_t converted() const;
```  
  
### <a name="return-value"></a>返回值  
 成功的转换数。  
  
### <a name="remarks"></a>备注  
 成功的转换数存储在转换计数对象中。  
  
##  <a name="from_bytes"></a>wstring_convert::from_bytes  
 将字节字符串转换为宽字符串。  
  
```
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`Byte`|要转换的单元素字节序列。|  
|`ptr`|要转换的以 null 结尾的 C 样式字符序列。|  
|`Bstr`|要转换的 [byte_string](#byte_string)。|  
|`first`|要转换的字符范围中的第一个字符。|  
|`last`|要转换的字符范围中的最后一个字符。|  
  
### <a name="return-value"></a>返回值  
 由转换生成的宽字符串对象。  
  
### <a name="remarks"></a>备注  
 如果[转换状态](../standard-library/wstring-convert-class.md)对象是使用显式值构造的 `not`，请在转换开始之前将它设置为其默认值（初始转换状态）。 否则保持不变。  
  
 成功转换的输入元素的数量存储在转换计数对象中。 如果未发生转换错误，则该成员函数返回转换后的宽字符串。 否则，如果对象是使用宽字符串错误消息的初始值设定项构造的，则该成员函数返回宽字符串错误消息对象。 否则，成员函数将引发 [range_error](../standard-library/range-error-class.md) 类的对象。  
  
##  <a name="int_type"></a>wstring_convert::int_type  
 表示整数的类型。  
  
```
typedef typename wide_string::traits_type::int_type int_type;
```  
  
### <a name="remarks"></a>备注  
 该类型是 `wide_string::traits_type::int_type` 的同义词。  
  
##  <a name="state"></a>wstring_convert::state  
 返回表示转换状态的对象。  
  
```
state_type state() const;
```  
  
### <a name="return-value"></a>返回值  
 [转换状态](../standard-library/wstring-convert-class.md)对象，表示转换的状态。  
  
### <a name="remarks"></a>备注  
  
##  <a name="state_type"></a>wstring_convert::state_type  
 表示转换状态的类型。  
  
```
typedef typename Codecvt::state_type state_type;
```  
  
### <a name="remarks"></a>备注  
 此类型描述一个可以表示转换状态的对象。 该类型是 `Codecvt::state_type` 的同义词。  
  
##  <a name="to_bytes"></a>wstring_convert::to_bytes  
 将宽字符串转换为字节字符串。  
  
```
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Char`|要转换的宽字符。|  
|`Wptr`|要转换的以 null 结尾的 C 样式序列（从 `wptr` 开始）。|  
|`Wstr`|要转换的 [wide_string](#wide_string)。|  
|`first`|要转换的元素范围内的第一个元素。|  
|`last`|要转换的元素范围内的最后一个元素。|  
  
### <a name="remarks"></a>备注  
 如果[转换状态](../standard-library/wstring-convert-class.md)对象是使用显式值构造的 `not`，请在转换开始之前将它设置为其默认值（初始转换状态）。 否则保持不变。  
  
 成功转换的输入元素的数量存储在转换计数对象中。 如果未发生转换错误，则成员函数返回转换后的字节字符串。 否则，如果对象是使用字节字符串错误消息的初始值设定项构造的，则成员函数返回字节字符串错误消息对象。 否则，成员函数将引发 [range_error](../standard-library/range-error-class.md) 类的对象。  
  
##  <a name="wide_string"></a>wstring_convert::wide_string  
 表示宽字符串的类型。  
  
```
typedef std::basic_string<Elem> wide_string;
```  
  
### <a name="remarks"></a>备注  
 该类型是 `std::basic_string<Elem>` 的同义词。  
  
##  <a name="wstring_convert"></a>wstring_convert::wstring_convert  
 构造 `wstring_convert` 类型的对象。  
  
```
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`*Pcvt`|用于执行转换的 `Codecvt` 类型的对象。|  
|`_State`|表示转换状态的 [state_type](#state_type) 类型的对象。|  
|`_Berr`|用于在发生错误时显示的 [byte_string](#byte_string)。|  
|`Werr`|用于在发生错误时显示的 [wide_string](#wide_string)。|  
  
### <a name="remarks"></a>备注  
 第一个构造函数将存储[转换对象](../standard-library/wstring-convert-class.md)中的 Pcvt_arg

