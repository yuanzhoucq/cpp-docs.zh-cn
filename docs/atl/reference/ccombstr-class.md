---
title: CComBSTR 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
ms.openlocfilehash: dd45c2ff9b43148e0fe27ebd410a2390a4d12ce2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497555"
---
# <a name="ccombstr-class"></a>CComBSTR 类

此类是[BSTR](/previous-versions/windows/desktop/automat/bstr)的包装器。

## <a name="syntax"></a>语法

```
class CComBSTR
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComBSTR:: CComBSTR](#ccombstr)|构造函数。|
|[CComBSTR:: ~ CComBSTR](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComBSTR::Append](#append)|将字符串追加到`m_str`。|
|[CComBSTR::AppendBSTR](#appendbstr)|将 BSTR 追加到`m_str`。|
|[CComBSTR::AppendBytes](#appendbytes)|向`m_str`添加指定的字节数。|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|从 safearray 中每个元素的第一个字符创建一个 BSTR, 并将其附加`CComBSTR`到对象。|
|[CComBSTR:: AssignBSTR](#assignbstr)|向`m_str`分配一个 BSTR。|
|[CComBSTR::Attach](#attach)|将 BSTR 附加到`CComBSTR`对象。|
|[CComBSTR::BSTRToArray](#bstrtoarray)|创建从零开始的一维 safearray, 其中数组的每个元素都是`CComBSTR`对象中的一个字符。|
|[CComBSTR::ByteLength](#bytelength)|返回的长度`m_str` (以字节为单位)。|
|[CComBSTR::Copy](#copy)|返回的副本`m_str`。|
|[CComBSTR::CopyTo](#copyto)|通过`m_str` **[out]** 参数返回的副本|
|[CComBSTR::Detach](#detach)|与对象分离`m_str` `CComBSTR` 。|
|[CComBSTR::Empty](#empty)|释放`m_str`。|
|[CComBSTR::Length](#length)|返回的长度`m_str`。|
|[CComBSTR::LoadString](#loadstring)|加载字符串资源。|
|[CComBSTR::ReadFromStream](#readfromstream)|从流中加载 BSTR 对象。|
|[CComBSTR::ToLower](#tolower)|将字符串转换为小写。|
|[CComBSTR::ToUpper](#toupper)|将字符串转换为大写。|
|[CComBSTR::WriteToStream](#writetostream)|保存`m_str`到流中。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CComBSTR:: operator BSTR](#operator_bstr)|`CComBSTR`将对象强制转换为 BSTR。|
|[CComBSTR:: operator!](#operator_not)|返回 TRUE 或 FALSE, 具体取决于`m_str`是否为 NULL。|
|[CComBSTR::operator !=](#operator_neq)|将`CComBSTR`与字符串进行比较。|
|[CComBSTR:: operator &](#operator_amp)|返回的`m_str`地址。|
|[CComBSTR:: operator + =](#operator_add_eq)|将追加`CComBSTR`到对象。|
|[CComBSTR:: operator <](#operator_lt)|将`CComBSTR`与字符串进行比较。|
|[CComBSTR:: operator =](#operator_eq)|向`m_str`赋值。|
|[CComBSTR:: operator = =](#operator_eq_eq)|将`CComBSTR`与字符串进行比较。|
|[CComBSTR:: operator >](#operator_gt)|将`CComBSTR`与字符串进行比较。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|包含与`CComBSTR`对象关联的 BSTR。|

## <a name="remarks"></a>备注

`CComBSTR`类是 bstr 的包装, 它是长度为前缀的字符串。 长度作为整数存储在字符串中的数据之前的内存位置。

在最后一次计数字符后, [BSTR](/previous-versions/windows/desktop/automat/bstr)以 null 结尾, 但也可能包含嵌入到字符串内的 null 字符。 字符串长度由字符计数确定, 而不是由第一个 null 字符决定。

> [!NOTE]
>  `CComBSTR`类提供了许多成员 (构造函数、赋值运算符和比较运算符), 这些成员采用 ANSI 或 Unicode 字符串作为参数。 这些函数的 ANSI 版本不如它们的 Unicode 对应, 因为通常在内部创建临时 Unicode 字符串。 为提高效率, 请尽可能使用 Unicode 版本。

> [!NOTE]
>  由于在 Visual Studio .net 中实现了改进的查找行为, 因此`bstr = L"String2" + bstr;`, 在以前的版本中可能编译的代码 (如) 应改为`bstr = CStringW(L"String2") + bstr`实现。

有关使用`CComBSTR`时的注意事项列表, 请参阅[使用 CComBSTR 进行编程](../../atl/programming-with-ccombstr-atl.md)。

## <a name="requirements"></a>要求

**标头:** atlbase。h

##  <a name="append"></a>CComBSTR:: Append

将*bstrSrc*的*lpsz*或 BSTR 成员追加到[m_str](#m_str)。

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>参数

*bstrSrc*<br/>
中要`CComBSTR`追加的对象。

*ch*<br/>
中要追加的字符。

*lpsz*<br/>
中要追加的以零结尾的字符串。 可以通过 LPCOLESTR 重载或 ANSI 字符串通过 LPCSTR 版本传递 Unicode 字符串。

*nLen*<br/>
中要追加的*lpsz*中的字符数。

### <a name="return-value"></a>返回值

如果成功, 则为 S_OK; 否则为任何标准的 HRESULT 错误值。

### <a name="remarks"></a>备注

在追加 ANSI 字符串之前, 它将转换为 Unicode 字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>CComBSTR:: AppendBSTR

向[m_str](#m_str)追加指定的 BSTR。

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
中要追加的 BSTR。

### <a name="return-value"></a>返回值

如果成功, 则为 S_OK; 否则为任何标准的 HRESULT 错误值。

### <a name="remarks"></a>备注

不要向此方法传递普通的宽字符字符串。 编译器无法捕获错误, 将发生运行时错误。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>CComBSTR:: AppendBytes

在不进行转换的情况下向[m_str](#m_str)追加指定的字节数。

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>参数

*lpsz*<br/>
中指向要追加的字节数组的指针。

*p*<br/>
中要追加的字节数。

### <a name="return-value"></a>返回值

如果成功, 则为 S_OK; 否则为任何标准的 HRESULT 错误值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>CComBSTR:: ArrayToBSTR

释放在`CComBSTR`对象中保存的任何现有字符串, 然后从 safearray 中每个元素的第一个字符创建一个 BSTR, 并将其`CComBSTR`附加到对象。

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>参数

*pSrc*<br/>
中包含用来创建字符串的元素的 safearray。

### <a name="return-value"></a>返回值

如果成功, 则为 S_OK; 否则为任何标准的 HRESULT 错误值。

##  <a name="assignbstr"></a>CComBSTR:: AssignBSTR

将 BSTR 分配给[m_str](#m_str)。

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>参数

*bstrSrc*<br/>
中要分配给当前`CComBSTR`对象的 BSTR。

### <a name="return-value"></a>返回值

如果成功, 则为 S_OK; 否则为任何标准的 HRESULT 错误值。

##  <a name="attach"></a>CComBSTR:: Attach

通过将[m_str](#m_str)成员设置`CComBSTR`为*src*, 将 BSTR 附加到对象。

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>参数

*src*<br/>
中要附加到对象的 BSTR。

### <a name="remarks"></a>备注

不要向此方法传递普通的宽字符字符串。 编译器无法捕获错误, 将发生运行时错误。

> [!NOTE]
>  如果`m_str`为非 NULL, 此方法将断言。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>CComBSTR:: BSTRToArray

创建从零开始的一维 safearray, 其中数组的每个元素都是`CComBSTR`对象中的一个字符。

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>参数

*ppArray*<br/>
弄指向用于保存函数结果的 safearray 的指针。

### <a name="return-value"></a>返回值

如果成功, 则为 S_OK; 否则为任何标准的 HRESULT 错误值。

##  <a name="bytelength"></a>CComBSTR:: ByteLength

返回中`m_str`的字节数, 不包括终止 null 字符。

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>返回值

[M_str](#m_str)成员的长度 (以字节为单位)。

### <a name="remarks"></a>备注

如果`m_str`为 NULL, 则返回0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>CComBSTR:: CComBSTR

构造函数。 默认构造函数将[m_str](#m_str)成员设置为 NULL。

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

*nSize*<br/>
中要从*sz*复制的字符数或的初始大小 (以字符为`CComBSTR`字符)。

*sz*<br/>
[in] 要复制的一个字符串。 Unicode 版本指定 LPCOLESTR;ANSI 版本指定了 LPCSTR。

*pSrc*<br/>
[in] 要复制的一个字符串。 Unicode 版本指定 LPCOLESTR;ANSI 版本指定了 LPCSTR。

*src*<br/>
[in] 一个 `CComBSTR` 对象。

*guid*<br/>
中对`GUID`结构的引用。

### <a name="remarks"></a>备注

复制构造函数将`m_str`设置为*src*的 BSTR 成员的副本。构造函数使用`StringFromGUID2`将 GUID 转换为字符串, 并存储结果。 `REFGUID`

其他构造函数将 `m_str` 设置为指定字符串的副本。 如果为*nSize*传递值, 则只会复制*nSize*字符, 后跟一个终止 null 字符。

`CComBSTR` 支持移动语义。 可以使用移动构造函数（采用右值引用 (`&&`) 来创建新对象的构造函数，该新对象使用与你作为自变量传入的旧对象相同的基础数据，而无需复制对象的开销。

析构函数释放由 `m_str` 指向的字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>CComBSTR:: ~ CComBSTR

析构函数。

```
~CComBSTR();
```

### <a name="remarks"></a>备注

析构函数释放由 `m_str` 指向的字符串。

##  <a name="copy"></a>CComBSTR:: Copy

分配并返回的`m_str`副本。

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>返回值

[M_str](#m_str)成员的副本。 如果`m_str`为 null, 则返回 null。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

##  <a name="copyto"></a>CComBSTR:: CopyTo

通过参数分配并返回[m_str](#m_str)的副本。

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>参数

*pbstr*<br/>
弄要在其中返回此方法所分配的字符串的 BSTR 的地址。

*pvarDest*<br/>
弄变体的地址, 返回此方法分配的字符串的形式。

### <a name="return-value"></a>返回值

表示副本成功或失败的标准 HRESULT 值。

### <a name="remarks"></a>备注

调用此方法后, *pvarDest*指向的变量将是 VT_BSTR 类型。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>CComBSTR::D etach

将[m_str](#m_str)与`CComBSTR`对象分离, 并`m_str`将设置为 NULL。

```
BSTR Detach() throw();
```

### <a name="return-value"></a>返回值

与`CComBSTR`对象关联的 BSTR。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>CComBSTR:: Empty

释放[m_str](#m_str)成员。

```
void Empty() throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

##  <a name="length"></a>CComBSTR:: Length

返回中`m_str`的字符数, 不包括终止 null 字符。

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>返回值

[M_str](#m_str)成员的长度。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>CComBSTR:: LoadString

加载由*nID*指定的字符串资源, 并将其存储在此对象中。

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>参数

请参阅 Windows SDK 中的[LoadString](/windows/win32/api/winuser/nf-winuser-loadstringw) 。

### <a name="return-value"></a>返回值

如果成功加载该字符串, 则返回 TRUE;否则, 返回 FALSE。

### <a name="remarks"></a>备注

第一个函数通过*hInst*参数从标识的模块加载资源。 第二个函数从与此项目中使用的[CComModule](../../atl/reference/ccommodule-class.md)派生对象关联的资源模块中加载资源。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>  CComBSTR::m_str

包含与`CComBSTR`对象关联的 BSTR。

```
BSTR m_str;
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>CComBSTR:: operator BSTR

`CComBSTR`将对象强制转换为 BSTR。

```
operator BSTR() const throw();
```

### <a name="remarks"></a>备注

允许您将对象`CComBSTR`传递给具有 **[in] BSTR**参数的函数。

### <a name="example"></a>示例

请参阅[CComBSTR:: m_str](#m_str)的示例。

##  <a name="operator_not"></a>CComBSTR:: operator!

检查 BSTR 字符串是否为 NULL。

```
bool operator!() const throw();
```

### <a name="return-value"></a>返回值

如果[m_str](#m_str)成员为 NULL, 则返回 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此运算符仅检查 NULL 值, 而不检查空字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>CComBSTR:: operator! =

返回[运算符 = =](#operator_eq_eq)的逻辑相反。

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>参数

*bstrSrc*<br/>
[in] 一个 `CComBSTR` 对象。

*pszSrc*<br/>
中以零结尾的字符串。

*nNull*<br/>
中必须为 NULL。

### <a name="return-value"></a>返回值

如果要比较的项与`CComBSTR`对象不相等, 则返回 TRUE; 否则, 返回 FALSE。

### <a name="remarks"></a>备注

`CComBSTR`在用户的默认区域设置的上下文中, 按秒进行比较。 最终比较运算符只是将包含的字符串与 NULL 进行比较。

##  <a name="operator_amp"></a>CComBSTR:: operator&amp;

返回存储在[m_str](#m_str)成员中的 BSTR 的地址。

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>备注

`CComBstr operator &`具有与之关联的特殊断言, 以帮助标识内存泄漏。 该程序将在初始化`m_str`成员时断言。 创建此断言是为了识别程序员使用`& operator`将新值分配给`m_str`成员而不释放第一次分配的`m_str`情况。 如果`m_str`等于 NULL, 则程序假定 m_str 尚未分配。 在这种情况下, 程序将不会进行断言。

默认情况下不启用此断言。 定义 ATL_CCOMBSTR_ADDRESS_OF_ASSERT 以启用此断言。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>CComBSTR:: operator + =

将字符串追加到`CComBSTR`对象。

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>参数

*bstrSrc*<br/>
中要`CComBSTR`追加的对象。

*pszSrc*<br/>
中要追加的以零结尾的字符串。

### <a name="remarks"></a>备注

`CComBSTR`在用户的默认区域设置的上下文中, 按秒进行比较。 LPCOLESTR 比较是使用`memcmp`每个字符串中的原始数据来完成的。 创建*pszSrc*的临时 Unicode 副本后, 将以相同的方式执行 LPCSTR 比较。 最终比较运算符只是将包含的字符串与 NULL 进行比较。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>CComBSTR:: operator&lt;

将`CComBSTR`与字符串进行比较。

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>返回值

如果要比较的项小于`CComBSTR`对象, 则返回 TRUE; 否则, 返回 FALSE。

### <a name="remarks"></a>备注

使用用户的默认区域设置执行比较。

##  <a name="operator_eq"></a>CComBSTR:: operator =

将[m_str](#m_str)成员设置为 *.psrc*的副本或*src*成员的一个副本。移动赋值运算符在移动`src`时不进行复制。

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>备注

*.Psrc*参数指定 Unicode 版本的 LPCOLESTR 或 ANSI 版本的 LPCSTR。

### <a name="example"></a>示例

请参阅[CComBSTR:: Copy](#copy)的示例。

##  <a name="operator_eq_eq"></a>CComBSTR:: operator = =

将`CComBSTR`与字符串进行比较。 `CComBSTR`在用户的默认区域设置的上下文中, 按秒进行比较。

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>参数

*bstrSrc*<br/>
[in] 一个 `CComBSTR` 对象。

*pszSrc*<br/>
中以零结尾的字符串。

*nNull*<br/>
中必须为 NULL。

### <a name="return-value"></a>返回值

如果要比较的项等于`CComBSTR`对象, 则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

最终比较运算符只是将包含的字符串与 NULL 进行比较。

##  <a name="operator_gt"></a>CComBSTR:: operator&gt;

将`CComBSTR`与字符串进行比较。

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>返回值

如果要比较的项大于`CComBSTR`对象, 则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

使用用户的默认区域设置执行比较。

##  <a name="readfromstream"></a>CComBSTR:: ReadFromStream

将[m_str](#m_str)成员设置为包含在指定流中的 BSTR。

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>参数

*pStream*<br/>
中指向包含数据的流上的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`ReadToStream`要求当前位置的流的内容与通过调用[WriteToStream](#writetostream)写出的数据格式兼容。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>CComBSTR:: ToLower

将包含的字符串转换为小写。

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

有关`CharLowerBuff`如何执行转换的详细信息, 请参阅。

##  <a name="toupper"></a>CComBSTR:: ToUpper

将包含的字符串转换为大写。

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

有关`CharUpperBuff`如何执行转换的详细信息, 请参阅。

##  <a name="writetostream"></a>CComBSTR:: WriteToStream

将[m_str](#m_str)成员保存到流中。

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>参数

*pStream*<br/>
中指向流上的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

可以使用[ReadFromStream](#readfromstream)函数从流的内容重新创建 BSTR。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)
