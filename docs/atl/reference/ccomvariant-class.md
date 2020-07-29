---
title: CComVariant 类
ms.date: 11/04/2016
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
ms.openlocfilehash: a435cf8e5501e4f21af53091dc0e28f1c1037379
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226563"
---
# <a name="ccomvariant-class"></a>CComVariant 类

此类包装变量类型，并提供指示所存储数据类型的成员。

## <a name="syntax"></a>语法

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComVariant：： CComVariant](#ccomvariant)|构造函数。|
|[CComVariant：： ~ CComVariant](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CComVariant：： Attach](#attach)|将变体附加到 `CComVariant` 对象。|
|[CComVariant：： ChangeType](#changetype)|将 `CComVariant` 对象转换为新类型。|
|[CComVariant：： Clear](#clear)|清除 `CComVariant` 对象。|
|[CComVariant：： Copy](#copy)|将变体复制到 `CComVariant` 对象。|
|[CComVariant：： CopyTo](#copyto)|复制对象的内容 `CComVariant` 。|
|[CComVariant：:D etach](#detach)|从对象中分离基础变体 `CComVariant` 。|
|[CComVariant：： GetSize](#getsize)|返回对象内容的大小（以字节为单位） `CComVariant` 。|
|[CComVariant：： ReadFromStream](#readfromstream)|从流加载变体。|
|[CComVariant：： SetByRef](#setbyref)|初始化 `CComVariant` 对象并将成员设置 `vt` 为 VT_BYREF。|
|[CComVariant：： WriteToStream](#writetostream)|将基础变体保存到流中。|

### <a name="public-operators"></a>公共运算符

|||
|-|-|
|[CComVariant：： operator <](#operator_lt)|指示对象是否 `CComVariant` 小于指定的变体。|
|[CComVariant：： operator >](#operator_gt)|指示对象是否 `CComVariant` 大于指定的变量。|
|[operator！ =](#operator_neq)|指示对象是否 `CComVariant` 不等于指定的变体。|
|[operator =](#operator_eq)|为 `CComVariant` 对象赋值。|
|[operator = =](#operator_eq_eq)|指示对象是否 `CComVariant` 等于指定的变量。|

## <a name="remarks"></a>备注

`CComVariant`包装 VARIANT 和 VARIANTARG 类型，它由一个联合和一个成员组成，该类型指示存储在联合中的数据的类型。 变体通常在自动化中使用。

`CComVariant`派生自变量类型，因此可以在可以使用变量的任何位置使用它。 例如，您可以使用 V_VT 宏来提取的类型， `CComVariant` 也可以 `vt` 直接访问成员，就像使用变体一样。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>要求

**标头：** atlcomcli。h

## <a name="ccomvariantattach"></a><a name="attach"></a>CComVariant：： Attach

安全地清除对象的当前内容 `CComVariant` ，将 *.psrc*的内容复制到此对象中，然后将 *.psrc*的变体类型设置为 VT_EMPTY。

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>参数

*.Psrc*<br/>
中指向要附加到对象的[变体](/windows/win32/api/oaidl/ns-oaidl-variant)。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

*.Psrc*保存的数据的所有权将转移到 `CComVariant` 对象。

## <a name="ccomvariantccomvariant"></a><a name="ccomvariant"></a>CComVariant：： CComVariant

每个构造函数通过调用 Win32 函数来处理对象的安全初始化， `CComVariant` `VariantInit` 或根据传递的参数设置对象的值和类型。

```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```

### <a name="parameters"></a>参数

*varSrc*<br/>
中`CComVariant`用于初始化对象的或变体 `CComVariant` 。 源变量的内容将复制到目标，而不进行转换。

*lpszSrc*<br/>
中用于初始化对象的字符串 `CComVariant` 。 可以将以零结尾的宽（Unicode）字符串传递到构造函数的 LPCOLESTR 版本或 LPCSTR 版本的 ANSI 字符串。 在任一情况下，都将字符串转换为使用分配的 Unicode BSTR `SysAllocString` 。 `CComVariant`将 VT_BSTR 对象的类型。

*bSrc*<br/>
中**`bool`** 用于初始化 `CComVariant` 对象的。 在 **`bool`** 存储之前，将参数转换为 VARIANT_BOOL。 `CComVariant`将 VT_BOOL 对象的类型。

*nSrc*<br/>
中**`int`**、 **BYTE**、 **`short`** 、、 **`long`** LONGLONG、ULONGLONG、、 **`unsigned short`** **`unsigned long`** 或 **`unsigned int`** 用于初始化 `CComVariant` 对象的。 对象的类型 `CComVariant` 将分别为 VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4 或 VT_UI4。

*vtSrc*<br/>
中变量的类型。 如果第一个参数为 **`int`** ，则 VT_I4 和 VT_INT 有效类型。 如果第一个参数为 **`long`** ，则 VT_I4 和 VT_ERROR 有效类型。 如果第一个参数为 **`double`** ，则 VT_R8 和 VT_DATE 有效类型。 如果第一个参数为 **`unsigned int`** ，则 VT_UI4 和 VT_UINT 有效类型。

*fltSrc*<br/>
中**`float`** 用于初始化 `CComVariant` 对象的。 `CComVariant`将 VT_R4 对象的类型。

*dblSrc*<br/>
中**`double`** 用于初始化 `CComVariant` 对象的。 `CComVariant`将 VT_R8 对象的类型。

*cySrc*<br/>
中`CY`用于初始化 `CComVariant` 对象的。 `CComVariant`将 VT_CY 对象的类型。

*.Psrc*<br/>
中`IDispatch` `IUnknown` 用于初始化对象的或指针 `CComVariant` 。 `AddRef`将在接口指针上调用。 对象的类型 `CComVariant` 将分别为 VT_DISPATCH 或 VT_UNKNOWN。

或用于初始化对象的 SAFERRAY 指针 `CComVariant` 。 SAFEARRAY 的副本存储在 `CComVariant` 对象中。 对象的类型 `CComVariant` 将为 SAFEARRAY 的原始类型和 VT_ARRAY 的组合。

*cSrc*<br/>
中**`char`** 用于初始化 `CComVariant` 对象的。 `CComVariant`将 VT_I1 对象的类型。

*bstrSrc*<br/>
中用于初始化对象的 BSTR `CComVariant` 。 `CComVariant`将 VT_BSTR 对象的类型。

### <a name="remarks"></a>备注

析构函数通过调用[CComVariant：： Clear](#clear)来管理清理。

## <a name="ccomvariantccomvariant"></a><a name="dtor"></a>CComVariant：： ~ CComVariant

析构函数。

```
~CComVariant() throw();
```

### <a name="remarks"></a>备注

此方法通过调用[CComVariant：： Clear](#clear)来管理清理。

## <a name="ccomvariantchangetype"></a><a name="changetype"></a>CComVariant：： ChangeType

将 `CComVariant` 对象转换为新类型。

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>参数

*vtNew*<br/>
中对象的新类型 `CComVariant` 。

*.Psrc*<br/>
中指向其值将转换为新类型的变量的指针。 默认值为 NULL，这意味着 `CComVariant` 将就地转换对象。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果为 *.psrc*传递值， `ChangeType` 将使用此变体作为转换的源。 否则， `CComVariant` 对象将为源。

## <a name="ccomvariantclear"></a><a name="clear"></a>CComVariant：： Clear

`CComVariant`通过调用 Win32 函数清除对象 `VariantClear` 。

```
HRESULT Clear();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

析构函数将自动调用 `Clear` 。

## <a name="ccomvariantcopy"></a><a name="copy"></a>CComVariant：： Copy

释放 `CComVariant` 对象，然后为其分配指定变量的副本。

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>参数

*.Psrc*<br/>
中指向要复制的[变量](/windows/win32/api/oaidl/ns-oaidl-variant)的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

## <a name="ccomvariantcopyto"></a><a name="copyto"></a>CComVariant：： CopyTo

复制对象的内容 `CComVariant` 。

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>参数

*pstrDest*<br/>
指向将接收对象内容副本的 BSTR `CComVariant` 。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`CComVariant`对象的类型必须是 VT_BSTR。

## <a name="ccomvariantdetach"></a><a name="detach"></a>CComVariant：:D etach

从对象中分离基础变体 `CComVariant` ，并将对象的类型设置为 VT_EMPTY。

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>参数

*pDest*<br/>
弄返回对象的基础变量值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

请注意， *pDest*引用的变量的内容将在分配给调用对象的值和类型之前自动清除 `CComVariant` 。

## <a name="ccomvariantgetsize"></a><a name="getsize"></a>CComVariant：： GetSize

对于简单固定的大小变体，此方法返回 **`sizeof`** 基础数据类型和**SIZEOF （VARTYPE）** 的值。

```
ULONG GetSize() const;
```

### <a name="return-value"></a>返回值

对象的当前内容的大小（以字节为单位） `CComVariant` 。

### <a name="remarks"></a>备注

如果变量包含接口指针，则 `GetSize` 查询 `IPersistStream` 或 `IPersistStreamInit` 。 如果成功，则返回值为 + 和返回的值的低序位32位 `GetSizeMax` `sizeof(CLSID)` `sizeof(VARTYPE)` 。 如果接口指针为 NULL，则 `GetSize` 返回 `sizeof(CLSID)` plus `sizeof(VARTYPE)` 。 如果总大小大于 ULONG_MAX，则 `GetSize` 返回 `sizeof(VARTYPE)` 表示错误的。

在所有其他情况下，从当前变量强制转换 VT_BSTR 类型的临时变量。 此 BSTR 的长度是按字符串长度加上字符串本身的长度加上空字符加上**sizeof （VARTYPE）** 的大小计算得出的。 如果无法将变量强制转换为 VT_BSTR 类型的变体，则 `GetSize` 返回**SIZEOF （VARTYPE）**。

此方法返回的大小与[CComVariant：： WriteToStream](#writetostream)在成功条件下使用的字节数相匹配。

## <a name="ccomvariantoperator-"></a><a name="operator_eq"></a>CComVariant：： operator =

向对象分配值和相应的类型 `CComVariant` 。

```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```

### <a name="parameters"></a>参数

*varSrc*<br/>
中`CComVariant`要分配给对象的或[变体](/windows/win32/api/oaidl/ns-oaidl-variant) `CComVariant` 。 源变量的内容将复制到目标，而不进行转换。

*bstrSrc*<br/>
中要分配给对象的 BSTR `CComVariant` 。 `CComVariant`将 VT_BSTR 对象的类型。

*lpszSrc*<br/>
中要分配给对象的字符串 `CComVariant` 。 可以将以零结尾的宽（Unicode）字符字符串传递到 LPCOLESTR 版本的运算符，或传递到 LPCSTR 版本的 ANSI 字符串。 在任一情况下，字符串都将转换为使用分配的 Unicode BSTR `SysAllocString` 。 `CComVariant`将 VT_BSTR 对象的类型。

*bSrc*<br/>
中**`bool`** 要分配给 `CComVariant` 对象的。 在 **`bool`** 存储之前，将参数转换为 VARIANT_BOOL。 `CComVariant`将 VT_BOOL 对象的类型。

*nSrc*<br/>
中**`int`** 要分配给对象的、BYTE、 **`short`** 、、 **`long`** LONGLONG、ULONGLONG、、 **`unsigned short`** **`unsigned long`** 或 **`unsigned int`** `CComVariant` 。 对象的类型 `CComVariant` 将分别为 VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4 或 VT_UI4。

*fltSrc*<br/>
中**`float`** 要分配给 `CComVariant` 对象的。 `CComVariant`将 VT_R4 对象的类型。

*dblSrc*<br/>
中**`double`** 要分配给 `CComVariant` 对象的。 `CComVariant`将 VT_R8 对象的类型。

*cySrc*<br/>
中`CY`要分配给 `CComVariant` 对象的。 `CComVariant`将 VT_CY 对象的类型。

*.Psrc*<br/>
中`IDispatch` `IUnknown` 要分配给对象的或指针 `CComVariant` 。 `AddRef`将在接口指针上调用。 对象的类型 `CComVariant` 将分别为 VT_DISPATCH 或 VT_UNKNOWN。

或，要分配给对象的 SAFEARRAY 指针 `CComVariant` 。 SAFEARRAY 的副本存储在 `CComVariant` 对象中。 对象的类型 `CComVariant` 将为 SAFEARRAY 的原始类型和 VT_ARRAY 的组合。

*cSrc*<br/>
中要分配给对象的字符 `CComVariant` 。 `CComVariant`将 VT_I1 对象的类型。

## <a name="ccomvariantoperator-"></a><a name="operator_eq_eq"></a>CComVariant：： operator = =

指示对象是否 `CComVariant` 等于指定的变量。

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果*varSrc*的值和类型与对象的值和类型分别相等，则返回 TRUE `CComVariant` 。 否则为 FALSE。 运算符使用用户的默认区域设置执行比较。

运算符仅比较变量类型的值。 它比较字符串、整数和浮点数，而不是数组或记录。

## <a name="ccomvariantoperator-"></a><a name="operator_neq"></a>CComVariant：： operator！ =

指示对象是否 `CComVariant` 不等于指定的变体。

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果*varSrc*的值或类型不等于对象的值或类型，则返回 TRUE `CComVariant` 。 否则为 FALSE。 运算符使用用户的默认区域设置执行比较。

运算符仅比较变量类型的值。 它比较字符串、整数和浮点数，而不是数组或记录。

## <a name="ccomvariantoperator-lt"></a><a name="operator_lt"></a>CComVariant：： operator&lt;

指示对象是否 `CComVariant` 小于指定的变体。

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果对象的值小于 VarSrc 的值，则返回 TRUE `CComVariant` 。 *varSrc* 否则为 FALSE。 运算符使用用户的默认区域设置执行比较。

## <a name="ccomvariantoperator-gt"></a><a name="operator_gt"></a>CComVariant：： operator&gt;

指示对象是否 `CComVariant` 大于指定的变量。

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果对象的值大于 VarSrc 的值，则返回 TRUE `CComVariant` 。 *varSrc* 否则为 FALSE。 运算符使用用户的默认区域设置执行比较。

## <a name="ccomvariantreadfromstream"></a><a name="readfromstream"></a>CComVariant：： ReadFromStream

将基础变体设置为指定流中包含的变体。

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>参数

*pStream*<br/>
中指向包含数据的流上的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`ReadToStream`需要对[WriteToStream](#writetostream)的前一次调用。

## <a name="ccomvariantsetbyref"></a><a name="setbyref"></a>CComVariant：： SetByRef

初始化 `CComVariant` 对象并将成员设置 `vt` 为 VT_BYREF。

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>参数

*T*<br/>
变体的类型，例如 BSTR、 **`int`** 或 **`char`** 。

*五*<br/>
用于初始化对象的指针 `CComVariant` 。

### <a name="remarks"></a>备注

`SetByRef`是一个函数模板，该模板将 `CComVariant` 对象初始化为指针*pT* ，并将成员设置 `vt` 为 VT_BYREF。 例如：

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

## <a name="ccomvariantwritetostream"></a><a name="writetostream"></a>CComVariant：： WriteToStream

将基础变体保存到流中。

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>参数

*pStream*<br/>
中指向流上的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
