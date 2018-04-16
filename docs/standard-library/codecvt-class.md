---
title: "codecvt 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocale/std::codecvt
- xlocale/std::codecvt::extern_type
- xlocale/std::codecvt::intern_type
- xlocale/std::codecvt::state_type
- xlocale/std::codecvt::always_noconv
- xlocale/std::codecvt::do_always_noconv
- xlocale/std::codecvt::do_encoding
- xlocale/std::codecvt::do_in
- xlocale/std::codecvt::do_length
- xlocale/std::codecvt::do_max_length
- xlocale/std::codecvt::do_out
- xlocale/std::codecvt::do_unshift
- xlocale/std::codecvt::encoding
- xlocale/std::codecvt::in
- xlocale/std::codecvt::length
- xlocale/std::codecvt::max_length
- xlocale/std::codecvt::out
- xlocale/std::codecvt::unshift
dev_langs:
- C++
helpviewer_keywords:
- std::codecvt [C++]
- std::codecvt [C++], extern_type
- std::codecvt [C++], intern_type
- std::codecvt [C++], state_type
- std::codecvt [C++], always_noconv
- std::codecvt [C++], do_always_noconv
- std::codecvt [C++], do_encoding
- std::codecvt [C++], do_in
- std::codecvt [C++], do_length
- std::codecvt [C++], do_max_length
- std::codecvt [C++], do_out
- std::codecvt [C++], do_unshift
- std::codecvt [C++], encoding
- std::codecvt [C++], in
- std::codecvt [C++], length
- std::codecvt [C++], max_length
- std::codecvt [C++], out
- std::codecvt [C++], unshift
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b456472fc28b473da29169acb899a1a8a142c095
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="codecvt-class"></a>codecvt 类
一种模板类，此模板类描述可用作区域设置 facet 的对象。 此模板类能够控制用于对程序中和程序外的字符进行编码的值序列之间的转换。  
  
## <a name="syntax"></a>语法  
  
```  
template <class CharType, class Byte, class StateType>  
class codecvt : public locale::facet, codecvt_base;  
```  
  
#### <a name="parameters"></a>参数  
 `CharType`  
 在程序中用于对字符进行编码的类型。  
  
 `Byte`  
 用于对程序外的字符进行编码的类型。  
  
 `StateType`  
 一种类型，此类型可用于表示字符表示形式的内部和外部类型之间转换的中间状态。  
  
## <a name="remarks"></a>备注  
 此模板类描述可用作[区域设置 facet](../standard-library/locale-class.md#facet_class) 的对象，用于控制 `CharType` 类型的值序列和 `Byte` 类型的值序列之间的转换。 `StateType` 类描述转换，`StateType` 类的对象存储转换期间的任何必要状态信息。  
  
 内部编码使用每个字符都包含固定字节数的表示形式，通常为 `char` 类型或 `wchar_t` 类型。  
  
 对于任何区域设置 facet，静态对象 `id` 的初始存储值为零。 首次尝试访问其存储值后，将在 `id` 中存储唯一正值。  
  
 [do_in](#do_in) 和 [do_out](#do_out) 的模板版本始终返回 `codecvt_base::noconv`。  
  
 C++ 标准库定义了若干显式专用化：  
  
 `template<>`  
  
 `codecvt<wchar_t, char, mbstate_t>`  
  
 在 `wchar_t` 和 `char` 序列之间转换。  
  
 `template<>`  
  
 `codecvt<char16_t, char, mbstate_t>`  
  
 在按 UTF-16 编码的 `char16_t` 序列和按 UTF-8 编码的 `char` 序列之间转换。  
  
 `template<>`  
  
 `codecvt<char32_t, char, mbstate_t>`  
  
 在按 UTF-32 (UCS-4) 编码的 `char32_t` 序列和按 UTF-8 编码的 `char` 序列之间转换。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[codecvt](#codecvt)|用作区域设置 facet 以处理转换的 `codecvt` 类的对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[extern_type](#extern_type)|用于外部表示形式的字符类型。|  
|[intern_type](#intern_type)|用于内部表示形式的字符类型。|  
|[state_type](#state_type)|一种字符类型，此类型用于表示内部和外部表示形式进行转换期间的中间状态。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[always_noconv](#always_noconv)|测试是否不需要完成转换。|  
|[do_always_noconv](#do_always_noconv)|为测试是否不需要完成转换而调用的虚拟函数。|  
|[do_encoding](#do_encoding)|测试 `Byte` 流的编码是否依赖于状态、使用的 `Byte` 数和生成的 `CharType` 数之间的比率是否一致（如果是，则确定此比率的值）的虚拟函数。|  
|[do_in](#do_in)|为将内部 `Byte` 序列转换为外部 `CharType` 序列而调用的虚拟函数。|  
|[do_length](#do_length)|确定给定外部 `Byte` 序列中有多少 `Byte` 生成的内部  `CharType` 不超过给定数量并返回此 `Byte` 数的虚拟函数。|  
|[do_max_length](#do_max_length)|返回生成一个内部 `CharType` 所需的最大外部字节数的虚拟函数。|  
|[do_out](#do_out)|为将内部 `CharType` 序列转换为外部字节序列而调用的虚拟函数。|  
|[do_unshift](#do_unshift)|一种虚拟函数，通过调用此函数可提供依赖于状态的转换中需要的 `Byte` 以完成 `Byte` 序列中的最后一个字符。|  
|[encoding](#encoding)|测试 `Byte` 流的编码是否依赖于状态、使用的 `Byte` 数和生成的 `CharType` 数之间的比率是否一致（如果是，则确定此比率的值）。|  
|[in](#in)|将 `Byte` 序列的外部表示形式转换为 `CharType` 序列的内部表示形式。|  
|[length](#length)|确定给定外部 `Byte` 序列中有多少 `Byte` 生成的内部  `CharType` 不超过给定数量，并返回此 `Byte` 数。|  
|[max_length](#max_length)|返回生成一个内部 `Byte` 所需的最大外部 `CharType` 数。|  
|[out](#out)|将内部 `CharType` 序列转换为外部 `Byte` 序列。|  
|[unshift](#unshift)|提供依赖于状态的转换中需要的外部 `Byte` 以完成 `Byte` 序列中的最后一个字符。|  
  
## <a name="requirements"></a>惠?  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
##  <a name="always_noconv"></a>  codecvt::always_noconv  
 测试是否不需要完成转换。  
  
```  
bool always_noconv() const throw();
```  
  
### <a name="return-value"></a>返回值  
 一个布尔值，如果不需要完成转换，则为 **true**；如果至少需要完成一个转换，则为 **false**。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_always_noconv](#do_always_noconv)。  
  
### <a name="example"></a>示例  
  
```cpp  
// codecvt_always_noconv.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >   
      ( loc ).always_noconv( );  
  
   if ( result1 )  
      cout << "No conversion is needed." << endl;  
   else  
      cout << "At least one conversion is required." << endl;  
  
   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >   
      ( loc ).always_noconv( );  
  
   if ( result2 )  
      cout << "No conversion is needed." << endl;  
   else  
      cout << "At least one conversion is required." << endl;  
}  
```  
  
```Output  
No conversion is needed.  
At least one conversion is required.  
```  
  
##  <a name="codecvt"></a>  codecvt::codecvt  
 用作区域设置 facet 以处理转换的 codecvt 类的对象的构造函数。  
  
```  
explicit codecvt(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>参数  
 `_Refs`  
 用于指定对象的内存管理类型的整数值。  
  
### <a name="remarks"></a>备注  
 `_Refs` 参数可能的值及其含义：  
  
-   0：对象的生存期由包含该对象的区域设置管理。  
  
-   1：必须手动管理对象的生存期。  
  
-   \> 1： 未定义这些值。  
  
 构造函数初始化其`locale::facet`与基对象**区域设置::**[方面](../standard-library/locale-class.md#facet_class)(`_Refs`)。  
  
##  <a name="do_always_noconv"></a>  codecvt::do_always_noconv  
 为测试是否不需要完成转换而调用的虚拟函数。  
  
```  
virtual bool do_always_noconv() const throw();
```  
  
### <a name="return-value"></a>返回值  
 只有每次调用 [do_in](#do_in) 或 [do_out](#do_out) 返回 **noconv** 时，受保护的虚拟成员函数才会返回 **true**。  
  
 模板版本始终返回 **true**。  
  
### <a name="example"></a>示例  
  请参阅 [always_noconv](#always_noconv) 的示例，它调用 `do_always_noconv`。  
  
##  <a name="do_encoding"></a>  codecvt::do_encoding  
 测试 **Byte** 流的编码是否依赖于状态、使用的 **Byte** 数和生成的 **CharType** 数之间的比率是否一致（如果是，则确定此比率的值）的虚拟函数。  
  
```  
virtual int do_encoding() const throw();
```  
  
### <a name="return-value"></a>返回值  
 受保护的虚拟成员函数返回：  
  
-   -1，如果类型序列的编码`extern_type`属于状态。  
  
-   如果编码涉及不同长度的序列，则为 0。  
  
- 如果编码仅涉及 *N* 长度的序列，则为 *N*  
  
### <a name="example"></a>示例  
  请参阅 [encoding](#encoding) 的示例，它调用 `do_encoding`。  
  
##  <a name="do_in"></a>  codecvt::do_in  
 为将外部 **Byte** 的序列转换为内部 **CharType** 序列而调用的虚拟函数。  
  
```  
virtual result do_in(
    StateType& _State,  
    const Byte* first1,   
    const Byte* last1,   
    const Byte*& next1,  
    CharType* first2,  
    CharType* last2,  
    CharType*& next2,) const;
```  
  
### <a name="parameters"></a>参数  
 `_State`  
 每次调用成员函数时保留的转换状态。  
  
 `first1`  
 指向待转换序列开头的指针。  
  
 `last1`  
 指向待转换序列末尾的指针。  
  
 `next1`  
 指向超出已转换序列末尾到第一个未转换字符的指针。  
  
 `first2`  
 指向已转换序列开头的指针。  
  
 `last2`  
 指向已转换序列末尾的指针。  
  
 `next2`  
 指向最后一个已转换的 **CharType** 后的 **CharType**，到目标序列中第一个未更改字符的指针。  
  
### <a name="return-value"></a>返回值  
 返回指示操作成功、部分成功或失败的值。 该函数返回：  
  
- 如果源序列格式不正确，则为 **codecvt_base::error**。  
  
- 如果函数不执行任何转换，则为 `codecvt_base::noconv`。  
  
- 如果转换成功，则为 **codecvt_base::ok**。  
  
- 如果源不足或目标大小不足以使转换成功完成，则为 **codecvt_base::partial**。  
  
### <a name="remarks"></a>备注  
 `_State` 必须代表新源序列开头的初始转换状态。 此函数根据需要来更改其存储的值以反映成功转换的当前状态。 否则未指定其存储的值。  
  
### <a name="example"></a>示例  
  请参阅 [in](#in) 的示例，它调用 `do_in`。  
  
##  <a name="do_length"></a>  codecvt::do_length  
 确定给定外部 **Byte** 序列中有多少 **Byte** 生成的内部 **CharType** 不超过给定数量并返回此 **Byte** 数的虚拟函数。  
  
```  
virtual int do_length(
    const StateType& _State,  
    const Byte* first1,   
    const Byte* last1,  
    size_t _Len2) const;
```  
  
### <a name="parameters"></a>参数  
 `_State`  
 每次调用成员函数时保留的转换状态。  
  
 `first1`  
 指向外部序列开头的指针。  
  
 `last1`  
 指向外部序列末尾的指针。  
  
 `_Len2`  
 成员函数可能会返回最大 **Byte** 数。  
  
### <a name="return-value"></a>返回值  
 一个表示转换的最大数量的计数的整数，不能超过由外部源序列在 [`first1`, `last1`) 中定义的 `_Len2`。  
  
### <a name="remarks"></a>备注  
 受保护的虚拟成员函数针对 `_State`（状态副本）、某些缓冲区 `_Buf`，及指针 `next1` 和 `next2` 有效调用 `do_in`（`_State`、`first1`、`last1`、`next1`、`_Buf`、`_Buf`  +  `_Len2`、`next2`）。  
  
 然后它返回`next2`  -  **buf**。 因此，它将计算的转换的最大数量，不能超过由源序列在 [`first1`, `last1`) 中定义的 `_Len2`。  
  
 模板版本始终返回较小的`last1`  -  `first1`和`_Len2`。  
  
### <a name="example"></a>示例  
  请参阅 [length](#length) 的示例，它调用 **do_length**。  
  
##  <a name="do_max_length"></a>  codecvt::do_max_length  
 返回生成一个内部 **CharType** 所需的最大外部 **Byte** 数的虚拟函数。  
  
```  
virtual int do_max_length() const throw();
```  
  
### <a name="return-value"></a>返回值  
 生成一个 **CharType** 所需的最大 **Byte** 数。  
  
### <a name="remarks"></a>备注  
 受保护的虚拟成员函数将返回可能由 [do_length](#do_length) (`first1`, `last1`, 1) 针对 `first1` 和 `last1` 的任意有效值返回的最大允许值。  
  
### <a name="example"></a>示例  
  请参阅 [max_length](#max_length) 的示例，它调用 `do_max_length`。  
  
##  <a name="do_out"></a>  codecvt::do_out  
 为将内部 **CharType** 的序列转换为外部 **Byte** 序列而调用的虚拟函数。  
  
```  
virtual result do_out(
    StateType& _State,  
    const CharType* first1,   
    const CharType* last1,  
    const CharType*& next1,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>参数  
 `_State`  
 每次调用成员函数时保留的转换状态。  
  
 `first1`  
 指向待转换序列开头的指针。  
  
 `last1`  
 指向待转换序列末尾的指针。  
  
 `next1`  
 引用指向最后一个已转换的 **CharType** 后的第一个未转换的 **CharType** 的指针。  
  
 `first2`  
 指向已转换序列开头的指针。  
  
 `last2`  
 指向已转换序列末尾的指针。  
  
 `next2`  
 引用指向最后一个已转换的 **Byte** 后的第一个未转换的 **Byte** 的指针。  
  
### <a name="return-value"></a>返回值  
 该函数返回：  
  
- 如果源序列格式不正确，则为 **codecvt_base::error**。  
  
- 如果函数不执行任何转换，则为 `codecvt_base::noconv`。  
  
- 如果转换成功，则为 **codecvt_base::ok**。  
  
- 如果源不足或目标大小不足以使转换成功完成，则为 **codecvt_base::partial**。  
  
### <a name="remarks"></a>备注  
 `_State` 必须代表新源序列开头的初始转换状态。 此函数根据需要来更改其存储的值以反映成功转换的当前状态。 否则未指定其存储的值。  
  
### <a name="example"></a>示例  
  请参阅 [out](#out) 的示例，它调用 `do_out`。  
  
##  <a name="do_unshift"></a>  codecvt::do_unshift  
 一种虚拟函数，通过调用此函数可提供依赖于状态的转换中需要的 **Byte** 以完成 **Byte** 序列中的最后一个字符。  
  
```  
virtual result do_unshift(
    StateType& _State,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>参数  
 `_State`  
 每次调用成员函数时保留的转换状态。  
  
 `first2`  
 指向目标范围内第一个位置的指针。  
  
 `last2`  
 指向目标范围内最后一个位置的指针。  
  
 `next2`  
 指向目标序列中第一个未更改元素的指针。  
  
### <a name="return-value"></a>返回值  
 该函数返回：  
  
- 如果 _*State*表示无效状态，则为 **codecvt_base::error**  
  
- 如果该函数不执行任何转换，则为 `codecvt_base::noconv`  
  
- 如果转换成功，则为 **codecvt_base::ok**  
  
- 如果目标大小不足以使转换成功完成，则为 **codecvt_base::partial**  
  
### <a name="remarks"></a>备注  
 受保护的虚拟成员函数尝试将源元素 **CharType**(0) 转换为其存储在 [ `first2`, `last2`) 中的目标序列，终止元素 **Byte**(0) 除外。 它始终存储在指向目标序列中第一个未更改元素的指针 `next2` 中。  
  
 _ *State* 必须代表新源序列开头的初始转换状态。 此函数根据需要来更改其存储的值以反映成功转换的当前状态。 通常情况下，转换源元素 **CharType**(0) 将使当前状态处于初始转换状态。  
  
### <a name="example"></a>示例  
  请参阅 [unshift](#unshift) 的示例，它调用 `do_unshift`。  
  
##  <a name="encoding"></a>  codecvt::encoding  
 测试 **Byte** 流的编码是否依赖于状态、使用的 **Byte** 数和生成的 **CharType** 数之间的比率是否一致（如果是，则确定此比率的值）。  
  
```  
int encoding() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果返回值为正，则该值是生成 **CharType** 字符所需的固定数目 **Byte**。  
  
 受保护的虚拟成员函数返回：  
  
-   -1，如果类型序列的编码`extern_type`属于状态。  
  
-   如果编码涉及不同长度的序列，则为 0。  
  
- 如果编码仅涉及 *N* 长度的序列，则为 *N*。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_encoding](#do_encoding)。  
  
### <a name="example"></a>示例  
  
```cpp  
// codecvt_encoding.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );  
   cout << result1 << endl;  
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );  
   cout << result1 << endl;  
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );  
   cout << result1 << endl;  
}  
```  
  
```Output  
1  
1  
1  
```  
  
##  <a name="extern_type"></a>  codecvt::extern_type  
 用于外部表示形式的字符类型。  
  
```  
typedef Byte extern_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **Byte** 的同义词。  
  
##  <a name="in"></a>  codecvt::in  
 将 **Byte** 序列的外部表示形式转换为 **CharType** 序列的内部表示形式。  
  
```  
result in(
    StateType& _State,  
    const Byte* first1,   
    const Byte* last1,   
    const Byte*& next1,  
    CharType* first2,  
    CharType* last2,  
    CharType*& next2,) const;
```  
  
### <a name="parameters"></a>参数  
 `_State`  
 每次调用成员函数时保留的转换状态。  
  
 `first1`  
 指向待转换序列开头的指针。  
  
 `last1`  
 指向待转换序列末尾的指针。  
  
 `next1`  
 指向超出已转换序列末尾到第一个未转换字符的指针。  
  
 `first2`  
 指向已转换序列开头的指针。  
  
 `last2`  
 指向已转换序列末尾的指针。  
  
 `next2`  
 指向最后一个已转换的 **Chartype** 后的 **CharType** 到目标序列中第一个未更改字符的指针。  
  
### <a name="return-value"></a>返回值  
 返回指示操作成功、部分成功或失败的值。 该函数返回：  
  
- 如果源序列格式不正确，则为 **codecvt_base::error**。  
  
- 如果函数不执行任何转换，则为 `codecvt_base::noconv`。  
  
- 如果转换成功，则为 **codecvt_base::ok**。  
  
- 如果源不足或目标大小不足以使转换成功完成，则为 **codecvt_base::partial**。  
  
### <a name="remarks"></a>备注  
 `_State` 必须代表新源序列开头的初始转换状态。 此函数根据需要来更改其存储的值以反映成功转换的当前状态。 部分转换后，必须设置 `_State` 以便在新字符到达时允许继续转换。  
  
 成员函数将返回 [do_in](#do_in)( `_State`, _ *First1,  last1,  next1, First2, _Llast2,  next2*)。  
  
### <a name="example"></a>示例  
  
```cpp  
// codecvt_in.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char* pszExt = "This is the string to be converted!";  
   wchar_t pwszInt [LEN+1];  
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));  
   const char* pszNext;  
   wchar_t* pwszNext;  
   mbstate_t state = {0};  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
     ( loc ).in( state,  
          pszExt, &pszExt[strlen(pszExt)], pszNext,  
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );  
   pwszInt[strlen(pszExt)] = 0;  
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )  
   << L"The converted string is:\n ["  
   << &pwszInt[0]  
   << L"]" << endl;  
   exit(-1);  
}  
```  
  
```Output  
It worked! The converted string is:  
 [This is the string to be converted!]  
```  
  
##  <a name="intern_type"></a>  codecvt::intern_type  
 用于内部表示形式的字符类型。  
  
```  
typedef CharType intern_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **CharType** 的同义词。  
  
##  <a name="length"></a>  codecvt::length  
 确定给定外部 **Byte** 序列中有多少 **Byte** 生成的内部 **CharType** 不超过给定数量，并返回此 **Byte** 数。  
  
```  
int length(
    const StateType& _State,  
    const Byte* first1,   
    const Byte* last1,  
    size_t _Len2) const;
```  
  
### <a name="parameters"></a>参数  
 `_State`  
 每次调用成员函数时保留的转换状态。  
  
 `first1`  
 指向外部序列开头的指针。  
  
 `last1`  
 指向外部序列末尾的指针。  
  
 `_Len2`  
 可由成员函数返回的最大字节数。  
  
### <a name="return-value"></a>返回值  
 一个表示转换的最大数量的计数的整数，不能超过由外部源序列在 [`first1`, `last1`) 中定义的 `_Len2`。  
  
### <a name="remarks"></a>备注  
 成员函数将返回 [do_length](#do_length)( *_State,  first1*, `last1`, `_Len2`)。  
  
### <a name="example"></a>示例  
  
```cpp  
// codecvt_length.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char* pszExt = "This is the string whose length is to be measured!";  
   mbstate_t state = {0};  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
     ( loc ).length( state,  
          pszExt, &pszExt[strlen(pszExt)], LEN );  
   cout << "The length of the string is: ";  
   wcout << res;  
   cout << "." << endl;  
   exit(-1);  
}  
```  
  
```Output  
The length of the string is: 50.  
```  
  
##  <a name="max_length"></a>  codecvt::max_length  
 返回生成一个内部 **CharType** 所需的最大外部 **Byte** 数。  
  
```  
int max_length() const throw();
```  
  
### <a name="return-value"></a>返回值  
 生成一个 **CharType** 所需的最大 **Byte** 数。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_max_length](#do_max_length)。  
  
### <a name="example"></a>示例  
  
```cpp  
// codecvt_max_length.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc( "C");//English_Britain" );//German_Germany  
   int res = use_facet<codecvt<char, char, mbstate_t> >  
     ( loc ).max_length( );  
   wcout << res << endl;  
}  
```  
  
```Output  
1  
```  
  
##  <a name="out"></a>  codecvt::out  
 将内部 **CharType** 序列转换为外部 **Byte** 序列。  
  
```  
result out(
    StateType& _State,  
    const CharType* first1,   
    const CharType* last1,  
    const CharType*& next1,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>参数  
 `_State`  
 每次调用成员函数时保留的转换状态。  
  
 `first1`  
 指向待转换序列开头的指针。  
  
 `last1`  
 指向待转换序列末尾的指针。  
  
 `next1`  
 引用指向最后一个已转换的 **CharType** 后的第一个未转换的 **CharType** 的指针。  
  
 `first2`  
 指向已转换序列开头的指针。  
  
 `last2`  
 指向已转换序列末尾的指针。  
  
 `next2`  
 引用指向最后一个已转换的 **Byte** 后的第一个未转换的 **Byte** 的指针。  
  
### <a name="return-value"></a>返回值  
 成员函数返回 [do_out](#do_out)( `_State`, `first1`, `last1`, `next1`, `first2`, `last2`, `next2`)。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅 [codecvt::do_out](#do_out)。  
  
### <a name="example"></a>示例  
  
```cpp  
// codecvt_out.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
#include <wchar.h>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char pszExt[LEN+1];  
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";  
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );  
   char* pszNext;  
   const wchar_t* pwszNext;  
   mbstate_t state;  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
      ( loc ).out( state,  
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,  
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );  
   pszExt[wcslen( pwszInt )] = 0;  
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )  
   << "The converted string is:\n ["  
   << &pszExt[0]  
   << "]" << endl;  
}  
```  
  
```Output  
It worked: The converted string is:  
 [This is the wchar_t string to be converted.]  
```  
  
##  <a name="state_type"></a>  codecvt::state_type  
 一种字符类型，此类型用于表示内部和外部表示形式进行转换期间的中间状态。  
  
```  
typedef StateType state_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **StateType**的同义词。  
  
##  <a name="unshift"></a>  codecvt::unshift  
 提供依赖于状态的转换中需要的 **Byte** 以完成 **Byte** 序列中的最后一个字符。  
  
```  
result unshift(
    StateType& _State,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>参数  
 `_State`  
 每次调用成员函数时保留的转换状态。  
  
 `first2`  
 指向目标范围内第一个位置的指针。  
  
 `last2`  
 指向目标范围内最后一个位置的指针。  
  
 `next2`  
 指向目标序列中第一个未更改元素的指针。  
  
### <a name="return-value"></a>返回值  
 该函数返回：  
  
- 如果状态表示无效状态，则为 **codecvt_base::error**。  
  
- 如果函数不执行任何转换，则为 `codecvt_base::noconv`。  
  
- 如果转换成功，则为 **codecvt_base::ok**。  
  
- 如果目标大小不足以使转换成功完成，则为 **codecvt_base::partial**。  
  
### <a name="remarks"></a>备注  
 受保护的虚拟成员函数尝试将源元素 **CharType**(0) 转换为其存储在 [ `first2`, `last2`) 中的目标序列，终止元素 **Byte**(0) 除外。 它始终存储在指向目标序列中第一个未更改元素的指针 `next2` 中。  
  
 `_State` 必须代表新源序列开头的初始转换状态。 此函数根据需要来更改其存储的值以反映成功转换的当前状态。 通常情况下，转换源元素 **CharType**(0) 将使当前状态处于初始转换状态。  
  
 成员函数返回 [do_unshift](#do_unshift)( `_State`, `first2`, `last2`, `next2` )。  
  
## <a name="see-also"></a>请参阅  
 [\<locale>](../standard-library/locale.md)   
 [代码页](../c-runtime-library/code-pages.md)   
 [区域设置名称、语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

