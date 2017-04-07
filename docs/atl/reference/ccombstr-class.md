---
title: "CComBSTR 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
dev_langs:
- C++
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 8cdedc5cfac9d49df812ae6fcfcc548201b1edb5
ms.openlocfilehash: e7b61a5826836e7d26a0d470631d7230f7b7be56
ms.lasthandoff: 02/24/2017

---
# <a name="ccombstr-class"></a>CComBSTR 类
此类是包装器`BSTR`s。  
  
## <a name="syntax"></a>语法  
  
```
class CComBSTR
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CComBSTR::CComBSTR](#ccombstr)|构造函数。|  
|[CComBSTR:: ~ CComBSTR](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComBSTR::Append](#append)|将字符串追加到`m_str`。|  
|[CComBSTR::AppendBSTR](#appendbstr)|追加`BSTR`到`m_str`。|  
|[CComBSTR::AppendBytes](#appendbytes)|追加到的字节指定的数目`m_str`。|  
|[CComBSTR::ArrayToBSTR](#arraytobstr)|创建`BSTR`safearray 中每个元素的第一个字符并将其附加到`CComBSTR`对象。|  
|[CComBSTR::AssignBSTR](#assignbstr)|将分配`BSTR`到`m_str`。|  
|[CComBSTR::Attach](#attach)|将附加`BSTR`到`CComBSTR`对象。|  
|[CComBSTR::BSTRToArray](#bstrtoarray)|创建的从零开始的一维 safearray，其中数组的每个元素都从字符`CComBSTR`对象。|  
|[CComBSTR::ByteLength](#bytelength)|返回的长度`m_str`以字节为单位。|  
|[CComBSTR::Copy](#copy)|返回一份`m_str`。|  
|[CComBSTR::CopyTo](#copyto)|返回一份`m_str`通过**[out 一个]**参数|  
|[CComBSTR::Detach](#detach)|分离`m_str`从`CComBSTR`对象。|  
|[CComBSTR::Empty](#empty)|释放`m_str`。|  
|[CComBSTR::Length](#length)|返回的长度`m_str`。|  
|[CComBSTR::LoadString](#loadstring)|加载字符串资源。|  
|[CComBSTR::ReadFromStream](#readfromstream)|加载`BSTR`从流对象。|  
|[CComBSTR::ToLower](#tolower)|将字符串转换为小写形式。|  
|[CComBSTR::ToUpper](#toupper)|将字符串转换为大写形式。|  
|[CComBSTR::WriteToStream](#writetostream)|将保存`m_str`到流。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CComBSTR::operator BSTR](#operator_bstr)|强制转换`CComBSTR`对象传递给`BSTR`。|  
|[CComBSTR::operator ！](#operator_not)|返回`true`或`false`，具体取决于`m_str`是`NULL`。|  
|[CComBSTR::operator ！ =](#operator_neq)|比较`CComBSTR`的字符串。|  
|[CComBSTR::operator.](#operator_amp)|返回的地址`m_str`。|  
|[CComBSTR::operator + =](#operator_add_eq)|追加`CComBSTR`的对象。|  
|[CComBSTR::operator](#operator_lt)|比较`CComBSTR`的字符串。|  
|[CComBSTR::operator =](#operator_eq)|将一个值赋给`m_str`。|  
|[CComBSTR::operator = =](#operator_eq_eq)|比较`CComBSTR`的字符串。|  
|[CComBSTR::operator&1;>](#operator_gt)|比较`CComBSTR`的字符串。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComBSTR::m_str](#m_str)|包含`BSTR`与关联`CComBSTR`对象。|  
  
## <a name="remarks"></a>备注  
 `CComBSTR`类是包装器`BSTR`秒，这是长度为前缀的字符串。 在前面的字符串中的数据的内存位置的整数存储长度。  
  
 一个[BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228)是以 null 结尾的之后最后一个字符计入，但还可能包含在字符串内嵌入的 null 字符。 字符串长度的字符数，而不是第一个空字符由决定。  
  
> [!NOTE]
>  `CComBSTR`类提供了许多采用 ANSI 或 Unicode 字符串作为参数的成员 （构造函数、 赋值运算符和比较运算符）。 这些函数的 ANSI 版本是它们对应的 Unicode 比效率更低，因为通常内部创建临时的 Unicode 字符串。 为了提高效率，请尽可能使用 Unicode 版本。  
  
> [!NOTE]
>  由于在 Visual Studio.NET 中实现的改进的查找行为，这段代码`bstr = L"String2" + bstr;`，这可能在早期版本中，已编译应当改为作为实现`bstr = CStringW(L"String2") + bstr`。  
  
 有关在使用时的注意事项列表`CComBSTR`，请参阅[使用 ccombstr 进行编程](../../atl/programming-with-ccombstr-atl.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
##  <a name="append"></a>CComBSTR::Append  
 追加是`lpsz`或`BSTR`的成员`bstrSrc`到[m_str](#m_str)。  
  
```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>参数  
 `bstrSrc`  
 [in]一个`CComBSTR`要追加的对象。  
  
 *ch*  
 [in]要追加的字符。  
  
 `lpsz`  
 [in]要追加的零结尾的字符字符串。 您可以传递通过一个 Unicode 字符串**LPCOLESTR**超负荷或通过非 ANSI 字符串`LPCSTR`版本。  
  
 `nLen`  
 [in]从的字符数`lpsz`追加。  
  
### <a name="return-value"></a>返回值  
 `S_OK`成功，则任何标准`HRESULT`错误值。  
  
### <a name="remarks"></a>备注  
 在追加之前，非 ANSI 字符串将转换为 Unicode。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&32;](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]  
  
##  <a name="appendbstr"></a>CComBSTR::AppendBSTR  
 指定将追加`BSTR`到[m_str](#m_str)。  
  
```
HRESULT AppendBSTR(BSTR p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 [in]一个`BSTR`追加。  
  
### <a name="return-value"></a>返回值  
 `S_OK`成功，则任何标准`HRESULT`错误值。  
  
### <a name="remarks"></a>备注  
 不将普通的宽字符字符串传递给此方法。 编译器不能捕获到的错误和运行的时将发生错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities 第&33;](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]  
  
##  <a name="appendbytes"></a>CComBSTR::AppendBytes  
 将追加到的字节指定的数[m_str](#m_str)而不进行转换。  
  
```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>参数  
 `lpsz`  
 [in]指向要追加的字节数组的指针。  
  
 `p`  
 [in]要追加的字节数。  
  
### <a name="return-value"></a>返回值  
 `S_OK`成功，则任何标准`HRESULT`错误值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&34;](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]  
  
##  <a name="arraytobstr"></a>CComBSTR::ArrayToBSTR  
 释放所有现有字符串保存在`CComBSTR`对象，然后创建`BSTR`safearray 中每个元素的第一个字符并将其附加到`CComBSTR`对象。  
  
```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```  
  
### <a name="parameters"></a>参数  
 `pSrc`  
 [in]Safearray，包含用于创建字符串的元素。  
  
### <a name="return-value"></a>返回值  
 `S_OK`成功，则任何标准`HRESULT`错误值。  
  
##  <a name="assignbstr"></a>CComBSTR::AssignBSTR  
 将分配`BSTR`到[m_str](#m_str)。  
  
```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```  
  
### <a name="parameters"></a>参数  
 `bstrSrc`  
 [in]一个`BSTR`要分配给当前`CComBSTR`对象。  
  
### <a name="return-value"></a>返回值  
 `S_OK`成功，则任何标准`HRESULT`错误值。  
  
##  <a name="attach"></a>CComBSTR::Attach  
 将附加`BSTR`到`CComBSTR`对象通过设置[m_str](#m_str)成员*src*。  
  
```
void Attach(BSTR src) throw();
```  
  
### <a name="parameters"></a>参数  
 *src*  
 [in]`BSTR`将附加到对象。  
  
### <a name="remarks"></a>备注  
 不将普通的宽字符字符串传递给此方法。 编译器不能捕获到的错误和运行的时将发生错误。  
  
> [!NOTE]
>  如果此方法将断定`m_str`为非**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&35;](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="bstrtoarray"></a>CComBSTR::BSTRToArray  
 创建的从零开始的一维 safearray，其中数组的每个元素都从字符`CComBSTR`对象。  
  
```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```  
  
### <a name="parameters"></a>参数  
 `ppArray`  
 [out]指向用来保存函数的结果的 safearray 的指针。  
  
### <a name="return-value"></a>返回值  
 `S_OK`成功，则任何标准`HRESULT`错误值。  
  
##  <a name="bytelength"></a>CComBSTR::ByteLength  
 返回中的字节数`m_str`，不包括终止 null 字符。  
  
```
unsigned int ByteLength() const throw();
```  
  
### <a name="return-value"></a>返回值  
 长度[m_str](#m_str)以字节为单位的成员。  
  
### <a name="remarks"></a>备注  
 否则，返回 0`m_str`是**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&36;](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]  
  
##  <a name="ccombstr"></a>CComBSTR::CComBSTR  
 构造函数。 默认构造函数集[m_str](#m_str)成员**NULL**。  
  
```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);  
CComBSTR(REFGUID  guid);  
CComBSTR(int nSize);  
CComBSTR(int nSize, LPCOLESTR sz);  
CComBSTR(int nSize, LPCSTR sz);  
CComBSTR(LPCOLESTR pSrc);  
CComBSTR(LPCSTR pSrc);  
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>参数  
 `nSize`  
 [in] 要从 `sz` 复制的字符数或 `CComBSTR` 的字符的初始大小。  
  
 `sz`  
 [in] 要复制的一个字符串。 指定的 Unicode 版本**LPCOLESTR**; 的 ANSI 版本指定`LPCSTR`。  
  
 `pSrc`  
 [in] 要复制的一个字符串。 指定的 Unicode 版本**LPCOLESTR**; 的 ANSI 版本指定`LPCSTR`。  
  
 *src*  
 [in] 一个 `CComBSTR` 对象。  
  
 `guid`  
 [in]对引用**GUID**结构。  
  
### <a name="remarks"></a>备注  
 复制构造函数集`m_str`一份到`BSTR`的成员*src*。 **REFGUID**构造函数将转换**GUID**字符串使用**StringFromGUID2**并存储结果。  
  
 其他构造函数将 `m_str` 设置为指定字符串的副本。 如果传递 `nSize` 的值则仅 `nSize` 字符将被复制，它后面是一个终止 null 字符。  
  
 `CComBSTR` 支持移动语义。 可以使用移动构造函数 (采用右值引用的构造函数 ( `&&`) 来创建新的对象为旧对象作为参数，而无需复制该对象的系统开销传递中使用相同的基础数据。  
  
 析构函数释放由 `m_str` 指向的字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&37;](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]  
  
##  <a name="dtor"></a>CComBSTR:: ~ CComBSTR  
 析构函数。  
  
```
~CComBSTR();
```  
  
### <a name="remarks"></a>备注  
 析构函数释放由 `m_str` 指向的字符串。  
  
##  <a name="copy"></a>CComBSTR::Copy  
 分配并返回一份`m_str`。  
  
```
BSTR Copy() const throw();
```  
  
### <a name="return-value"></a>返回值  
 一份[m_str](#m_str)成员。 If `m_str` is **NULL**, returns **NULL**.  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&38;](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]  
  
##  <a name="copyto"></a>CComBSTR::CopyTo  
 分配并返回一份[m_str](#m_str)通过参数。  
  
```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```  
  
### <a name="parameters"></a>参数  
 *pbstr*  
 [out]地址`BSTR`顺序返回此方法分配的字符串。  
  
 `pvarDest`  
 [out]地址**VARIANT**顺序返回此方法分配的字符串。  
  
### <a name="return-value"></a>返回值  
 一种标准`HRESULT`值，该值指示是成功还是失败的副本。  
  
### <a name="remarks"></a>备注  
 调用此方法后**VARIANT**指向`pvarDest`的类型将为`VT_BSTR`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&39;](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]  
  
##  <a name="detach"></a>CComBSTR::Detach  
 分离[m_str](#m_str)从`CComBSTR`对象并设置`m_str`到**NULL**。  
  
```
BSTR Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 `BSTR`与关联`CComBSTR`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&40;](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]  
  
##  <a name="empty"></a>CComBSTR::Empty  
 释放[m_str](#m_str)成员。  
  
```
void Empty() throw();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&41;](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]  
  
##  <a name="length"></a>CComBSTR::Length  
 返回中的字符数`m_str`，不包括终止 null 字符。  
  
```
unsigned int Length() const throw();
```  
  
### <a name="return-value"></a>返回值  
 长度[m_str](#m_str)成员。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&42;](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]  
  
##  <a name="loadstring"></a>CComBSTR::LoadString  
 加载指定的字符串资源`nID`并将其存储在此对象中。  
  
```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```  
  
### <a name="parameters"></a>参数  
 请参阅[LoadString](http://msdn.microsoft.com/library/windows/desktop/ms647486)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 返回**true**如果字符串为成功加载; 否则为返回**false**。  
  
### <a name="remarks"></a>备注  
 第一个函数从由您通过标识的模块加载资源`hInst`参数。 第二个函数从与关联的资源模块加载资源[CComModule](../../atl/reference/ccommodule-class.md)-派生此项目中使用的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&43;](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]  
  
##  <a name="m_str"></a>CComBSTR::m_str  
 包含`BSTR`与关联`CComBSTR`对象。  
  
```
BSTR m_str;
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&49;](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]  
  
##  <a name="operator_bstr"></a>CComBSTR::operator BSTR  
 强制转换`CComBSTR`对象传递给`BSTR`。  
  
```  
operator BSTR() const throw();
```  
  
### <a name="remarks"></a>备注  
 可用于传递`CComBSTR`对具有函数的对象**[in] BSTR**参数。  
  
### <a name="example"></a>示例  
 请参阅示例[CComBSTR::m_str](#m_str)。  
  
##  <a name="operator_not"></a>CComBSTR::operator ！  
 检查是否`BSTR`字符串为 NULL。  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回**true**如果[m_str](#m_str)成员是**NULL**; 否则为**false**。  
  
### <a name="remarks"></a>备注  
 此运算符仅检查 NULL 值，不为空字符串。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&35;](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="operator_neq"></a>CComBSTR::operator ！ =  
 返回的逻辑反[运算符 = =](#operator_eq_eq)。  
  
```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```  
  
### <a name="parameters"></a>参数  
 `bstrSrc`  
 [in] 一个 `CComBSTR` 对象。  
  
 `pszSrc`  
 [in]以零结尾的字符串。  
  
 `nNull`  
 [in]必须是**NULL**。  
  
### <a name="return-value"></a>返回值  
 返回**true**要比较的项是否不等于`CComBSTR`对象; 否则，返回**false**。  
  
### <a name="remarks"></a>备注  
 `CComBSTR`s 文本比较用户的默认区域设置的上下文中。 最后一个比较运算符仅比较该字符串包含与**NULL**。  
  
##  <a name="operator_amp"></a>CComBSTR::operator&amp;  
 返回的地址`BSTR`存储在[m_str](#m_str)成员。  
  
```
BSTR* operator&() throw();
```  
  
### <a name="remarks"></a>备注  
 `CComBstr operator &`具有与之来帮助确定内存泄漏关联的特殊的断言。 该程序将断言时`m_str`成员初始化。 创建此断言是为了确定在哪些情况其中一名程序员都使用`& operator`若要将新值赋给`m_str`未释放的第一次分配成员`m_str`。 如果`m_str`等于 NULL，则该程序假定该 m_str 不尚未分配。 在这种情况下，该程序将不断言。  
  
 默认情况下不启用此断言。 定义`ATL_CCOMBSTR_ADDRESS_OF_ASSERT`若要启用此断言。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&46;](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities #&47;](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]  
  
##  <a name="operator_add_eq"></a>CComBSTR::operator + =  
 将字符串追加到`CComBSTR`对象。  
  
```
CComBSTR& operator+= (const CComBSTR& bstrSrc);  
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```  
  
### <a name="parameters"></a>参数  
 `bstrSrc`  
 [in]一个`CComBSTR`要追加的对象。  
  
 `pszSrc`  
 [in]要追加以零结尾的字符串。  
  
### <a name="remarks"></a>备注  
 `CComBSTR`s 文本比较用户的默认区域设置的上下文中。 **LPCOLESTR**进行比较使用`memcmp`中每个字符串的原始数据。 `LPCSTR`比较执行相同的方式后一种临时的将复制的 Unicode`pszSrc`已创建。 最后一个比较运算符仅比较该字符串包含与**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&48;](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]  
  
##  <a name="operator_lt"></a>CComBSTR::operator&lt;  
 比较`CComBSTR`的字符串。  
  
```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回**true**要比较的项是否小于`CComBSTR`对象; 否则，返回**false**。  
  
### <a name="remarks"></a>备注  
 使用用户的默认区域设置进行比较。  
  
##  <a name="operator_eq"></a>CComBSTR::operator =  
 集[m_str](#m_str)成员与一份`pSrc`或一份`BSTR`的成员*src*。 移动赋值运算符将移动`src`而不复制该项。   
  
```
CComBSTR& operator= (const CComBSTR& src);  
CComBSTR& operator= (LPCOLESTR pSrc);  
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```  
  
### <a name="remarks"></a>备注  
 `pSrc`参数指定任一**LPCOLESTR** Unicode 版本或`LPCSTR`的 ANSI 版本。  
  
### <a name="example"></a>示例  
 请参阅示例[CComBSTR::Copy](#copy)。  
  
##  <a name="operator_eq_eq"></a>CComBSTR::operator = =  
 比较`CComBSTR`的字符串。 `CComBSTR`s 文本比较用户的默认区域设置的上下文中。  
  
```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```  
  
### <a name="parameters"></a>参数  
 `bstrSrc`  
 [in] 一个 `CComBSTR` 对象。  
  
 `pszSrc`  
 [in]以零结尾的字符串。  
  
 `nNull`  
 [in]必须是**NULL**。  
  
### <a name="return-value"></a>返回值  
 返回**true**要比较的项是否等于`CComBSTR`对象; 否则，返回**false**。  
  
### <a name="remarks"></a>备注  
 最后一个比较运算符仅比较该字符串包含与**NULL**。  
  
##  <a name="operator_gt"></a>CComBSTR::operator&gt;  
 比较`CComBSTR`的字符串。  
  
```
bool operator>(const CComBSTR& bstrSrc) const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回**true**要比较的项是否大于`CComBSTR`对象; 否则，返回**false**。  
  
### <a name="remarks"></a>备注  
 使用用户的默认区域设置进行比较。  
  
##  <a name="readfromstream"></a>CComBSTR::ReadFromStream  
 集[m_str](#m_str)成员`BSTR`包含在指定的流。  
  
```
HRESULT ReadFromStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 [in]一个指向[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)上包含数据的流接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 **ReadToStream**需要的内容流中的当前位置，以将与数据格式写出，通过调用兼容[WriteToStream](#writetostream)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&44;](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]  
  
##  <a name="tolower"></a>CComBSTR::ToLower  
 将包含的字符串转换为小写形式。  
  
```
HRESULT ToLower() throw();
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 请参阅**CharLowerBuff**有关如何执行转换的详细信息。  
  
##  <a name="toupper"></a>CComBSTR::ToUpper  
 将包含的字符串转换为大写形式。  
  
```
HRESULT ToUpper() throw();
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 请参阅**CharUpperBuff**有关如何执行转换的详细信息。  
  
##  <a name="writetostream"></a>CComBSTR::WriteToStream  
 将保存[m_str](#m_str)到流的成员。  
  
```
HRESULT WriteToStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 [in]一个指向[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)流上的接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 你可以重新创建流使用的内容从 BSTR [ReadFromStream](#readfromstream)函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&45;](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [ATL 和 MFC 字符串转换宏](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)

