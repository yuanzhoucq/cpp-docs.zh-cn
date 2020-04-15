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
ms.openlocfilehash: adaad47c49a64c6654b70fa60ef5514e104c50a5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321053"
---
# <a name="ccombstr-class"></a>CComBSTR 类

此类是[BSTR](/previous-versions/windows/desktop/automat/bstr)的包装。

## <a name="syntax"></a>语法

```
class CComBSTR
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComBSTR：CComBSTR](#ccombstr)|构造函数。|
|[CComBSTR：*CComBSTR](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComBSTR：：附录](#append)|将字符串追加到`m_str`。|
|[CComBSTR：：附录BSTR](#appendbstr)|将 BSTR 追加`m_str`到 。|
|[CComBSTR：：附加字节](#appendbytes)|将指定数量的字节追加到`m_str`。|
|[CComBSTR：：ArraytoBSTR](#arraytobstr)|从安全数组中每个元素的第一个字符创建 BSTR 并将其`CComBSTR`附加到对象。|
|[CComBSTR：：分配BSTR](#assignbstr)|将 BSTR 分配给`m_str`。|
|[CComBSTR：：附加](#attach)|将 BSTR 附加到`CComBSTR`对象。|
|[CComBSTR：BSTRToarray](#bstrtoarray)|创建基于零的一维安全数组，其中数组的每个元素都是对象中的`CComBSTR`字符。|
|[CComBSTR：字节长度](#bytelength)|返回以字节为单位`m_str`的长度。|
|[CComBSTR：复制](#copy)|返回 的副本`m_str`。|
|[CComBSTR：：复制到](#copyto)|通过`m_str`**[out]** 参数返回 的副本|
|[CComBSTR：:D](#detach)|`m_str`从`CComBSTR`对象分离。|
|[CComBSTR：空](#empty)|自由。 `m_str`|
|[CComBSTR：长度](#length)|返回 的长度`m_str`。|
|[CComBSTR：：加载字符串](#loadstring)|加载字符串资源。|
|[CComBSTR：从流中阅读](#readfromstream)|从流加载 BSTR 对象。|
|[CComBSTR：：到下](#tolower)|将字符串转换为小写。|
|[CComBSTR：：上部](#toupper)|将字符串转换为大写。|
|[CComBSTR：：写入流](#writetostream)|保存到`m_str`流。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CComBSTR：：操作员BSTR](#operator_bstr)|将`CComBSTR`对象强制转换为 BSTR。|
|[CComBSTR：：操作员！](#operator_not)|返回 TRUE 或 FALSE，`m_str`具体取决于是否为 NULL。|
|[CComBSTR：：操作员！*](#operator_neq)|将`CComBSTR`和 字符串进行比较。|
|[CComBSTR：：操作员&](#operator_amp)|返回 的地址`m_str`。|
|[CComBSTR：：操作员 |](#operator_add_eq)|将 a`CComBSTR`追加到对象。|
|[CComBSTR：：操作员<](#operator_lt)|将`CComBSTR`和 字符串进行比较。|
|[CComBSTR：：操作员 |](#operator_eq)|将值分配给`m_str`。|
|[CComBSTR：：操作员 |](#operator_eq_eq)|将`CComBSTR`和 字符串进行比较。|
|[CComBSTR：：操作员>](#operator_gt)|将`CComBSTR`和 字符串进行比较。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComBSTR：m_str](#m_str)|包含与`CComBSTR`对象关联的 BSTR。|

## <a name="remarks"></a>备注

类`CComBSTR`是 BtR 的包装器，它是长度预固定字符串。 长度以整数存储在字符串中数据之前的内存位置。

[BSTR](/previous-versions/windows/desktop/automat/bstr)在最后一个计数字符后为 null 终止，但也可能包含嵌入在字符串中的空字符。 字符串长度由字符计数（而不是第一个空字符）确定。

> [!NOTE]
> 该`CComBSTR`类提供许多成员（构造函数、赋值运算符和比较运算符），这些成员将 ANSI 或 Unicode 字符串作为参数。 这些函数的 ANSI 版本的效率低于 Unicode 版本，因为临时 Unicode 字符串通常是在内部创建的。 为提高效率，请尽可能使用 Unicode 版本。

> [!NOTE]
> 由于在 Visual Studio .NET 中实现了改进的查找行为，`bstr = L"String2" + bstr;`因此，在以前的版本中可能编译的代码（如 ）应作为`bstr = CStringW(L"String2") + bstr`实现。

有关使用`CComBSTR`时的注意事项列表，请参阅[使用 CComBSTR 编程](../../atl/programming-with-ccombstr-atl.md)。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccombstrappend"></a><a name="append"></a>CComBSTR：：附录

将*lpsz*或*bstrSrc*的 BSTR 成员m_str [。](#m_str)

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>参数

*布斯特施尔*<br/>
[在]要`CComBSTR`追加的对象。

*ch*<br/>
[在]要追加的字符。

*lpsz*<br/>
[在]要追加的零端接字符串。 您可以通过 LPCOLESTR 重载传递 Unicode 字符串，也可以通过 LPCSTR 版本传递 ANSI 字符串。

*nLen*<br/>
[在]从*lpsz*到追加的字符数。

### <a name="return-value"></a>返回值

成功S_OK或任何标准的 HRESULT 错误值。

### <a name="remarks"></a>备注

在追加之前，ANSI 字符串将转换为 Unicode。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

## <a name="ccombstrappendbstr"></a><a name="appendbstr"></a>CComBSTR：：附录BSTR

将指定的 BSTR 追加到[m_str](#m_str)。

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
[在]要追加的 BSTR。

### <a name="return-value"></a>返回值

成功S_OK或任何标准的 HRESULT 错误值。

### <a name="remarks"></a>备注

不要将普通宽字符字符串传递给此方法。 编译器无法捕获错误，并且将发生运行时错误。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

## <a name="ccombstrappendbytes"></a><a name="appendbytes"></a>CComBSTR：：附加字节

将指定的字节数追加[到m_str](#m_str)而不进行转换。

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>参数

*lpsz*<br/>
[在]指向要追加的字节数组的指针。

*P*<br/>
[在]要追加的字节数。

### <a name="return-value"></a>返回值

成功S_OK或任何标准的 HRESULT 错误值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

## <a name="ccombstrarraytobstr"></a><a name="arraytobstr"></a>CComBSTR：：ArraytoBSTR

释放`CComBSTR`对象中保留的任何现有字符串，然后从安全数组中每个元素的第一个字符创建一个 BSTR 并将其附加到`CComBSTR`对象。

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>参数

*pSrc*<br/>
[在]包含用于创建字符串的元素的安全数组。

### <a name="return-value"></a>返回值

成功S_OK或任何标准的 HRESULT 错误值。

## <a name="ccombstrassignbstr"></a><a name="assignbstr"></a>CComBSTR：：分配BSTR

将 BSTR 分配给[m_str](#m_str)。

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>参数

*布斯特施尔*<br/>
[在]要分配给当前`CComBSTR`对象的 BSTR。

### <a name="return-value"></a>返回值

成功S_OK或任何标准的 HRESULT 错误值。

## <a name="ccombstrattach"></a><a name="attach"></a>CComBSTR：：附加

通过将`CComBSTR`[m_str](#m_str)成员设置为*src，* 将 BSTR 附加到对象。

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>参数

*src*<br/>
[在]要附加到对象的 BSTR。

### <a name="remarks"></a>备注

不要将普通宽字符字符串传递给此方法。 编译器无法捕获错误，并且将发生运行时错误。

> [!NOTE]
> 如果`m_str`为非 NULL，则此方法将断言。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstrbstrtoarray"></a><a name="bstrtoarray"></a>CComBSTR：BSTRToarray

创建基于零的一维安全数组，其中数组的每个元素都是对象中的`CComBSTR`字符。

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>参数

*ppArray*<br/>
[出]指向用于保存函数结果的安全数组的指针。

### <a name="return-value"></a>返回值

成功S_OK或任何标准的 HRESULT 错误值。

## <a name="ccombstrbytelength"></a><a name="bytelength"></a>CComBSTR：字节长度

返回 中的`m_str`字节数，不包括终止空字符。

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>返回值

[m_str](#m_str)成员的长度（以字节为单位）。

### <a name="remarks"></a>备注

如果为`m_str`NULL，则返回 0。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

## <a name="ccombstrccombstr"></a><a name="ccombstr"></a>CComBSTR：CComBSTR

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
[在]要从*sz*复制的字符数或 以`CComBSTR`字符 表示的初始大小。

*深圳*<br/>
[in] 要复制的一个字符串。 Unicode 版本指定 LPCOLESTR;ANSI 版本指定 LPCSTR。

*pSrc*<br/>
[in] 要复制的一个字符串。 Unicode 版本指定 LPCOLESTR;ANSI 版本指定 LPCSTR。

*src*<br/>
[in] 一个 `CComBSTR` 对象。

*Guid*<br/>
[在]对结构的`GUID`引用。

### <a name="remarks"></a>备注

复制构造函数将设置`m_str`到*src*的 BSTR 成员的副本。 构造`REFGUID`函数使用 并将 GUID 转换为字符串`StringFromGUID2`并存储结果。

其他构造函数将 `m_str` 设置为指定字符串的副本。 如果传递*nSize 的值*，则只复制*nSize*字符，后跟终止空字符。

`CComBSTR` 支持移动语义。 可以使用移动构造函数（采用右值引用 (`&&`) 来创建新对象的构造函数，该新对象使用与你作为自变量传入的旧对象相同的基础数据，而无需复制对象的开销。

析构函数释放由 `m_str` 指向的字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

## <a name="ccombstrccombstr"></a><a name="dtor"></a>CComBSTR：*CComBSTR

析构函数。

```
~CComBSTR();
```

### <a name="remarks"></a>备注

析构函数释放由 `m_str` 指向的字符串。

## <a name="ccombstrcopy"></a><a name="copy"></a>CComBSTR：复制

分配并返回 的副本`m_str`。

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>返回值

[m_str](#m_str)成员的副本。 如果`m_str`为 NULL，则返回 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

## <a name="ccombstrcopyto"></a><a name="copyto"></a>CComBSTR：：复制到

通过 参数分配并返回[m_str](#m_str)的副本。

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>参数

*pbstr*<br/>
[出]返回此方法分配的字符串的 BSTR 的地址。

*普瓦尔德斯特*<br/>
[出]要返回此方法分配的字符串的 VARIANT 的地址。

### <a name="return-value"></a>返回值

指示副本成功或失败的标准 HRESULT 值。

### <a name="remarks"></a>备注

调用此方法后 *，pvarDest*指向的 VARIANT 将称为类型VT_BSTR。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

## <a name="ccombstrdetach"></a><a name="detach"></a>CComBSTR：:D

从`CComBSTR`对象分离`m_str`[m_str](#m_str)并设置为 NULL。

```
BSTR Detach() throw();
```

### <a name="return-value"></a>返回值

与`CComBSTR`对象关联的 BSTR。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

## <a name="ccombstrempty"></a><a name="empty"></a>CComBSTR：空

释放[m_str](#m_str)成员。

```
void Empty() throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

## <a name="ccombstrlength"></a><a name="length"></a>CComBSTR：长度

返回 中的`m_str`字符数，不包括终止空字符。

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>返回值

[m_str](#m_str)成员的长度。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

## <a name="ccombstrloadstring"></a><a name="loadstring"></a>CComBSTR：：加载字符串

加载*nID*指定的字符串资源并将其存储在此对象中。

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>参数

请参阅 Windows SDK 中的[加载字符串](/windows/win32/api/winuser/nf-winuser-loadstringw)。

### <a name="return-value"></a>返回值

如果已成功加载字符串，则返回 TRUE;如果字符串已成功加载，则返回 TRUE。否则，返回 FALSE。

### <a name="remarks"></a>备注

第一个函数通过*hInst*参数从您标识的模块加载资源。 第二个函数从与本项目中使用的[CComModule](../../atl/reference/ccommodule-class.md)派生对象关联的资源模块中加载资源。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

## <a name="ccombstrm_str"></a><a name="m_str"></a>CComBSTR：m_str

包含与`CComBSTR`对象关联的 BSTR。

```
BSTR m_str;
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

## <a name="ccombstroperator-bstr"></a><a name="operator_bstr"></a>CComBSTR：：操作员BSTR

将`CComBSTR`对象强制转换为 BSTR。

```
operator BSTR() const throw();
```

### <a name="remarks"></a>备注

允许您将对象传递给`CComBSTR`具有 **[in] BSTR**参数的函数。

### <a name="example"></a>示例

请参阅[CComBSTR 的示例：：m_str](#m_str)。

## <a name="ccombstroperator-"></a><a name="operator_not"></a>CComBSTR：：操作员！

检查 BSTR 字符串是否为 NULL。

```
bool operator!() const throw();
```

### <a name="return-value"></a>返回值

如果[m_str](#m_str)成员为 NULL，则返回 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此运算符仅检查 NULL 值，而不是检查空字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_neq"></a>CComBSTR：：操作员！*

返回[运算符 #](#operator_eq_eq)的逻辑相反。

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>参数

*布斯特施尔*<br/>
[in] 一个 `CComBSTR` 对象。

*皮茨斯尔克*<br/>
[在]零端接字符串。

*nNull*<br/>
[在]必须为 NULL。

### <a name="return-value"></a>返回值

如果要比较的项不等于对象，`CComBSTR`则返回 TRUE;否则，返回 FALSE。

### <a name="remarks"></a>备注

`CComBSTR`在用户的默认区域设置的上下文中以文本方式进行比较。 最后的比较运算符只是将包含的字符串与 NULL 进行比较。

## <a name="ccombstroperator-amp"></a><a name="operator_amp"></a>CComBSTR：：操作员&amp;

返回存储在[m_str](#m_str)成员中的 BSTR 地址。

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>备注

`CComBstr operator &`具有与其关联的特殊断言，以帮助识别内存泄漏。 当成员初始化时，`m_str`程序将断言。 创建此断言是为了识别程序员使用`& operator`在不释放 的第一个分配的情况下向`m_str`成员分配新值的情况。 `m_str` 如果`m_str`等于 NULL，则程序假定尚未分配m_str。 在这种情况下，程序不会断言。

默认情况下，未启用此断言。 定义ATL_CCOMBSTR_ADDRESS_OF_ASSERT以启用此断言。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_add_eq"></a>CComBSTR：：操作员 |

将字符串追加到对象。 `CComBSTR`

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>参数

*布斯特施尔*<br/>
[在]要`CComBSTR`追加的对象。

*皮茨斯尔克*<br/>
[在]要追加的零端接字符串。

### <a name="remarks"></a>备注

`CComBSTR`在用户的默认区域设置的上下文中以文本方式进行比较。 LPCOLESTR 比较使用`memcmp`每个字符串中的原始数据来完成。 创建*pszSrc*的临时 Unicode 副本后，以相同的方式执行 LPCSTR 比较。 最后的比较运算符只是将包含的字符串与 NULL 进行比较。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

## <a name="ccombstroperator-lt"></a><a name="operator_lt"></a>CComBSTR：：操作员&lt;

将`CComBSTR`和 字符串进行比较。

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>返回值

如果要比较的项小于对象，`CComBSTR`则返回 TRUE;否则，返回 FALSE。

### <a name="remarks"></a>备注

比较使用用户的默认区域设置执行。

## <a name="ccombstroperator-"></a><a name="operator_eq"></a>CComBSTR：：操作员 |

将[m_str](#m_str)成员设置为*pSrc*的副本或*src*的 BSTR 成员的副本。 移动分配运算符移动`src`而不复制它。

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>备注

*pSrc*参数为 Unicode 版本指定 LPCOLESTR，为 ANSI 版本指定 LPCSTR。

### <a name="example"></a>示例

请参阅[CComBSTR 的示例：：复制](#copy)。

## <a name="ccombstroperator-"></a><a name="operator_eq_eq"></a>CComBSTR：：操作员 |

将`CComBSTR`和 字符串进行比较。 `CComBSTR`在用户的默认区域设置的上下文中以文本方式进行比较。

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>参数

*布斯特施尔*<br/>
[in] 一个 `CComBSTR` 对象。

*皮茨斯尔克*<br/>
[在]零端接字符串。

*nNull*<br/>
[在]必须为 NULL。

### <a name="return-value"></a>返回值

如果要比较的项等于对象，`CComBSTR`则返回 TRUE;否则，返回 FALSE。

### <a name="remarks"></a>备注

最后的比较运算符只是将包含的字符串与 NULL 进行比较。

## <a name="ccombstroperator-gt"></a><a name="operator_gt"></a>CComBSTR：：操作员&gt;

将`CComBSTR`和 字符串进行比较。

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>返回值

如果要比较的项大于对象，`CComBSTR`则返回 TRUE;否则，返回 FALSE。

### <a name="remarks"></a>备注

比较使用用户的默认区域设置执行。

## <a name="ccombstrreadfromstream"></a><a name="readfromstream"></a>CComBSTR：从流中阅读

将[m_str](#m_str)成员设置到指定流中包含的 BSTR。

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>参数

*pStream*<br/>
[在]指向流中包含数据的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

`ReadToStream`要求当前位置的流内容与[WriteToStream](#writetostream)调用时写入的数据格式兼容。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

## <a name="ccombstrtolower"></a><a name="tolower"></a>CComBSTR：：到下

将包含的字符串转换为小写。

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

有关如何`CharLowerBuff`执行转换的详细信息，请参阅。

## <a name="ccombstrtoupper"></a><a name="toupper"></a>CComBSTR：：上部

将包含的字符串转换为大写。

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

有关如何`CharUpperBuff`执行转换的详细信息，请参阅。

## <a name="ccombstrwritetostream"></a><a name="writetostream"></a>CComBSTR：：写入流

将[m_str](#m_str)成员保存到流中。

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>参数

*pStream*<br/>
[在]指向流上的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

您可以使用[ReadFromStream](#readfromstream)函数从流的内容中重新创建 BSTR。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)
