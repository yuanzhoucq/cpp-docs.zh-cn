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
ms.openlocfilehash: 6a6ad49533028dbcb8c45b63c55a51090533137e
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522477"
---
# <a name="ccomvariant-class"></a>CComVariant 类

此类包装提供存储的数据类型，该值指示成员的变体类型。

## <a name="syntax"></a>语法

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|构造函数。|
|[CComVariant:: ~ CComVariant](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComVariant::Attach](#attach)|将附加到一个变体`CComVariant`对象。|
|[CComVariant::ChangeType](#changetype)|将转换`CComVariant`为新类型的对象。|
|[CComVariant::Clear](#clear)|清除`CComVariant`对象。|
|[CComVariant::Copy](#copy)|将复制到一个变体`CComVariant`对象。|
|[CComVariant::CopyTo](#copyto)|内容复制`CComVariant`对象。|
|[CComVariant::Detach](#detach)|从基础的变体中分离`CComVariant`对象。|
|[CComVariant::GetSize](#getsize)|返回中的内容的字节数大小`CComVariant`对象。|
|[CComVariant::ReadFromStream](#readfromstream)|从流加载一个变体。|
|[CComVariant::SetByRef](#setbyref)|初始化`CComVariant`对象并设置`vt`VT_BYREF 的成员。|
|[CComVariant::WriteToStream](#writetostream)|将保存到流的基础的变体。|

### <a name="public-operators"></a>公共运算符

|||
|-|-|
|[CComVariant::operator <](#operator_lt)|指示是否`CComVariant`对象是否小于指定的变体。|
|[CComVariant::operator >](#operator_gt)|指示是否`CComVariant`对象是否大于指定的变体。|
|[运算符 ！ =](#operator_neq)|指示是否`CComVariant`对象不等于指定的变体。|
|[operator =](#operator_eq)|将一个值赋给`CComVariant`对象。|
|[operator ==](#operator_eq_eq)|指示是否`CComVariant`对象等于指定的变体。|

## <a name="remarks"></a>备注

`CComVariant` 包装 VARIANT 和 VARIANTARG 类型，其中包含联合和联合中存储的数据类型，该值指示成员。 在自动化中通常使用变体。

`CComVariant` 派生于变体类型，因此可以使用一个变体的位置，可以使用它。 例如，可以使用 V_VT 宏的类型中提取`CComVariant`，或可以访问`vt`成员直接就像可以使用一个变体。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>要求

**标头：** atlcomcli.h

##  <a name="attach"></a>  CComVariant::Attach

安全地清除当前的内容`CComVariant`对象，请将复制的内容*pSrc*成此对象，然后设置的变体类型*pSrc*为 VT_EMPTY。

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>参数

*pSrc*<br/>
[in]指向[变体](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)要附加到对象。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

保存的数据的所有权*pSrc*传输到`CComVariant`对象。

##  <a name="ccomvariant"></a>  CComVariant::CComVariant

每个构造函数将处理的安全初始化`CComVariant`对象通过调用`VariantInit`Win32 函数或通过设置对象的值与根据传递的参数的类型。

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
[in]`CComVariant`或用来初始化的变体`CComVariant`对象。 源变体的内容复制到目标而不进行转换。

*lpszSrc*<br/>
[in]用于初始化的字符字符串`CComVariant`对象。 可以将零终止宽 (Unicode) 字符字符串传递给构造函数或 ANSI 字符串到 LPCSTR 版本的 LPCOLESTR 版本。 在任一情况下，此字符串将转换为 Unicode 使用分配的 BSTR `SysAllocString`。 类型`CComVariant`对象将成为 VT_BSTR。

*bSrc*<br/>
[in]**Bool**用来初始化`CComVariant`对象。 **Bool**参数转换为 VARIANT_BOOL 再将其存储。 类型`CComVariant`对象都是 VT_BOOL。

*nSrc*<br/>
[in]**Int**，**字节**，**短**，**长**，LONGLONG、 ULONGLONG， **unsigned short**， **无符号长**，或**无符号的 int**用来初始化`CComVariant`对象。 类型`CComVariant`对象将分别为 VT_I4、 VT_UI1、 VT_I2、 VT_I4、 为 VT_I8、 VT_UI8、 VT_UI2、 VT_UI4 或 VT_UI4。

*vtSrc*<br/>
[in]变体类型。 当第一个参数是**int**，有效类型为 VT_I4 和 VT_INT。 当第一个参数是**长**，有效类型为 VT_I4 和 VT_ERROR。 当第一个参数是**double**，有效类型是 VT_R8 和 VT_DATE。 当第一个参数是**无符号的 int**，有效类型是 VT_UI4 和 VT_UINT。

*fltSrc*<br/>
[in]**Float**用来初始化`CComVariant`对象。 类型`CComVariant`对象将成为 VT_R4。

*dblSrc*<br/>
[in]**双**用来初始化`CComVariant`对象。 类型`CComVariant`对象将成为 VT_R8。

*cySrc*<br/>
[in]`CY`用来初始化`CComVariant`对象。 类型`CComVariant`对象将成为 VT_CY。

*pSrc*<br/>
[in]`IDispatch`或`IUnknown`指针用于初始化`CComVariant`对象。 `AddRef` 将接口指针上调用。 类型`CComVariant`对象将分别为 VT_DISPATCH 或 VT_UNKNOWN。

或者，用来初始化 SAFERRAY 指针`CComVariant`对象。 SAFEARRAY 的副本存储在`CComVariant`对象。 类型`CComVariant`对象将是原始类型的 SAFEARRAY 和 VT_ARRAY 的组合。

*cSrc*<br/>
[in]**Char**用来初始化`CComVariant`对象。 类型`CComVariant`对象将成为 VT_I1。

*bstrSrc*<br/>
[in]BSTR 用于初始化`CComVariant`对象。 类型`CComVariant`对象将成为 VT_BSTR。

### <a name="remarks"></a>备注

析构函数通过调用管理清理[CComVariant::Clear](#clear)。

##  <a name="dtor"></a>  CComVariant:: ~ CComVariant

析构函数。

```
~CComVariant() throw();
```

### <a name="remarks"></a>备注

此方法通过调用管理清理[CComVariant::Clear](#clear)。

##  <a name="changetype"></a>  CComVariant::ChangeType

将转换`CComVariant`为新类型的对象。

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>参数

*vtNew*<br/>
[in]新类型`CComVariant`对象。

*pSrc*<br/>
[in]一个指向其值将转换为新类型的变体。 默认值为 NULL，含义`CComVariant`将就地转换对象。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

如果传递的值*pSrc*，`ChangeType`将使用此变体作为源进行转换。 否则为`CComVariant`对象将成为源。

##  <a name="clear"></a>  CComVariant::Clear

清除`CComVariant`对象通过调用`VariantClear`Win32 函数。

```
HRESULT Clear();
```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

析构函数自动调用`Clear`。

##  <a name="copy"></a>  CComVariant::Copy

释放`CComVariant`对象，然后将其分配指定的变体的副本。

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>参数

*pSrc*<br/>
[in]一个指向[变体](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)要复制。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="copyto"></a>  CComVariant::CopyTo

内容复制`CComVariant`对象。

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>参数

*pstrDest*<br/>
指向将接收的内容的副本的 BSTR`CComVariant`对象。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`CComVariant`对象必须是类型 VT_BSTR。

##  <a name="detach"></a>  CComVariant::Detach

从基础的变体中分离`CComVariant`对象，并将该对象的类型设置为 VT_EMPTY。

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>参数

*pDest*<br/>
[out]返回对象的基础的变体值。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

请注意，该变体的内容引用的*pDest*的值和调用类型在赋值前会自动清除`CComVariant`对象。

##  <a name="getsize"></a>  CComVariant::GetSize

对于简单的固定大小变体，此方法返回**sizeof**加上的基础数据类型**sizeof(VARTYPE)**。

```
ULONG GetSize() const;
```

### <a name="return-value"></a>返回值

以字节为单位的当前内容的大小`CComVariant`对象。

### <a name="remarks"></a>备注

如果该变量包含的接口指针，`GetSize`中查询`IPersistStream`或`IPersistStreamInit`。 如果成功，，则返回值是个返回的值的低 32 位`GetSizeMax`再加上**sizeof** CLSID 并**sizeof(VARTYPE)**。 如果接口指针为 NULL，`GetSize`将返回**sizeof** CLSID 加号**sizeof(VARTYPE)**。 如果总大小大于 ULONG_MAX，`GetSize`将返回**sizeof(VARTYPE)** 指示错误。

在所有其他情况下，从当前变量强制转换类型 VT_BSTR 的临时变体。 此 BSTR 的长度计算为字符串的长度再加上字符串本身的长度的大小加上加号的 null 字符的大小**sizeof(VARTYPE)**。 如果将该变量不能强制转换为类型 VT_BSTR、 的变体`GetSize`将返回**sizeof(VARTYPE)**。

此方法返回的大小匹配的使用的字节数[CComVariant::WriteToStream](#writetostream)成功的情况下。

##  <a name="operator_eq"></a>  CComVariant::operator =

分配值和相应类型设置为`CComVariant`对象。

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
[in]`CComVariant`或[变体](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)要分配给`CComVariant`对象。 源变体的内容复制到目标而不进行转换。

*bstrSrc*<br/>
[in]要分配给的 BSTR`CComVariant`对象。 类型`CComVariant`对象将成为 VT_BSTR。

*lpszSrc*<br/>
[in]要分配给字符串`CComVariant`对象。 可以将零终止宽 (Unicode) 字符字符串传递给 LPCOLESTR 版本的运算符或到 LPCSTR 版本为 ANSI 字符串。 在任一情况下，此字符串将转换为 Unicode 使用分配的 BSTR `SysAllocString`。 类型`CComVariant`对象将成为 VT_BSTR。

*bSrc*<br/>
[in]**Bool**要分配给`CComVariant`对象。 **Bool**参数转换为 VARIANT_BOOL 再将其存储。 类型`CComVariant`对象都是 VT_BOOL。

*nSrc*<br/>
[in]**Int**，字节**短**，**长**，LONGLONG、 ULONGLONG， **unsigned short**，**无符号长**，或**无符号的 int**要分配给`CComVariant`对象。 类型`CComVariant`对象将分别为 VT_I4、 VT_UI1、 VT_I2、 VT_I4、 为 VT_I8、 VT_UI8、 VT_UI2、 VT_UI4 或 VT_UI4。

*fltSrc*<br/>
[in]**Float**要分配给`CComVariant`对象。 类型`CComVariant`对象将成为 VT_R4。

*dblSrc*<br/>
[in]**双**要分配给`CComVariant`对象。 类型`CComVariant`对象将成为 VT_R8。

*cySrc*<br/>
[in]`CY`要分配给`CComVariant`对象。 类型`CComVariant`对象将成为 VT_CY。

*pSrc*<br/>
[in]`IDispatch`或`IUnknown`指针分配给`CComVariant`对象。 `AddRef` 将接口指针上调用。 类型`CComVariant`对象将分别为 VT_DISPATCH 或 VT_UNKNOWN。

或者，若要分配给的 SAFEARRAY 指针`CComVariant`对象。 SAFEARRAY 的副本存储在`CComVariant`对象。 类型`CComVariant`对象将是原始类型的 SAFEARRAY 和 VT_ARRAY 的组合。

*cSrc*<br/>
[in]要分配给 char`CComVariant`对象。 类型`CComVariant`对象将成为 VT_I1。

##  <a name="operator_eq_eq"></a>  CComVariant::operator = =

指示是否`CComVariant`对象等于指定的变体。

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果返回 TRUE 值和类型*varSrc*等于的值和类型，分别的`CComVariant`对象。 否则为 FALSE。 运算符使用用户的默认区域设置进行比较。

运算符仅变量类型的值进行比较。 比较字符串、 整数和浮点点，但不是数组或记录。

##  <a name="operator_neq"></a>  CComVariant::operator ！ =

指示是否`CComVariant`对象不等于指定的变体。

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果返回 TRUE 的值或类型*varSrc*不等于的值或类型，分别的`CComVariant`对象。 否则为 FALSE。 运算符使用用户的默认区域设置进行比较。

运算符仅变量类型的值进行比较。 比较字符串、 整数和浮点点，但不是数组或记录。

##  <a name="operator_lt"></a>  CComVariant::operator &lt;

指示是否`CComVariant`对象是否小于指定的变体。

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果返回 TRUE 的值`CComVariant`对象是否小于的值*varSrc*。 否则为 FALSE。 运算符使用用户的默认区域设置进行比较。

##  <a name="operator_gt"></a>  CComVariant::operator &gt;

指示是否`CComVariant`对象是否大于指定的变体。

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果返回 TRUE 的值`CComVariant`对象是否大于的值*varSrc*。 否则为 FALSE。 运算符使用用户的默认区域设置进行比较。

##  <a name="readfromstream"></a>  CComVariant::ReadFromStream

设置指定流中包含的变体的基础变体。

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>参数

*pStream*<br/>
[in]一个指向[IStream](/windows/desktop/api/objidl/nn-objidl-istream)上包含数据的流接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

`ReadToStream` 要求对以前调用[WriteToStream](#writetostream)。

##  <a name="setbyref"></a>  CComVariant::SetByRef

初始化`CComVariant`对象并设置`vt`VT_BYREF 的成员。

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>参数

*T*<br/>
变体，例如，BSTR，类型**int**，或**char**。

*pT*<br/>
用于初始化的指针`CComVariant`对象。

### <a name="remarks"></a>备注

`SetByRef` 是一个函数模板，初始化`CComVariant`对象的指针*pT* ，并设置`vt`VT_BYREF 的成员。 例如：

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>  CComVariant::WriteToStream

将保存到流的基础的变体。

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>参数

*pStream*<br/>
[in]一个指向[IStream](/windows/desktop/api/objidl/nn-objidl-istream)流上的接口。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)