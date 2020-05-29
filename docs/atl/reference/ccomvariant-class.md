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
ms.openlocfilehash: 9a84d91e20242fb206d1d3f71fcb3dd207561f62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327230"
---
# <a name="ccomvariant-class"></a>CComVariant 类

此类包装 VARIANT 类型，提供一个成员，指示存储的数据类型。

## <a name="syntax"></a>语法

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCom变量：Ccom变量](#ccomvariant)|构造函数。|
|[CCom变量：*Ccom变量](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom 变量：：附加](#attach)|将 VARIANT 附加到`CComVariant`对象。|
|[CCom 变量：更改类型](#changetype)|将`CComVariant`对象转换为新类型。|
|[CCom 变量：清除](#clear)|清除`CComVariant`对象。|
|[CCom 变量：复制](#copy)|将 VARIANT 复制到`CComVariant`对象。|
|[Ccom 变量：：复制到](#copyto)|复制`CComVariant`对象的内容。|
|[CComVariant：:Detach](#detach)|从`CComVariant`对象分离基础 VARIANT。|
|[CCom 变量：获取 Size](#getsize)|返回`CComVariant`对象内容的大小（以字节数为单位）。|
|[Ccom 变量：：从流中读取](#readfromstream)|从流加载 VARIANT。|
|[Ccom 变量：：设置ByRef](#setbyref)|初始化对象并将`CComVariant``vt`成员设置为VT_BYREF。|
|[Ccom 变量：：写入流](#writetostream)|将基础 VARIANT 保存到流中。|

### <a name="public-operators"></a>公共运算符

|||
|-|-|
|[CComVariant：：操作员<](#operator_lt)|指示`CComVariant`对象是否小于指定的 VARIANT。|
|[CComVariant：：操作员>](#operator_gt)|指示`CComVariant`对象是否大于指定的 VARIANT。|
|[操作员 ！]](#operator_neq)|指示`CComVariant`对象是否等于指定的 VARIANT。|
|[运算符 |](#operator_eq)|向`CComVariant`对象分配值。|
|[运算符 |](#operator_eq_eq)|指示`CComVariant`对象是否等于指定的 VARIANT。|

## <a name="remarks"></a>备注

`CComVariant`包装 VARIANT 和 VARIANTARG 类型，该类型由一个联合和一个成员组成，指示联盟中存储的数据类型。 VARIANT 通常用于自动化。

`CComVariant`派生自 VARIANT 类型，因此可以在可以使用 VARIANT 的任何位置使用。 例如，可以使用V_VT宏提取 类型，`CComVariant`也可以像使用 VARIANT 一样直接访问`vt`成员。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>要求

**标题：** atlcomcli.h

## <a name="ccomvariantattach"></a><a name="attach"></a>CCom 变量：：附加

安全地清除`CComVariant`对象的当前内容，将*pSrc*的内容复制到此对象中，然后将*pSrc*的变体类型设置为VT_EMPTY。

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>参数

*pSrc*<br/>
[在]指向要附加到对象的[VARIANT。](/windows/win32/api/oaidl/ns-oaidl-variant)

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

*pSrc*持有的数据的所有权将转移到对象。 `CComVariant`

## <a name="ccomvariantccomvariant"></a><a name="ccomvariant"></a>CCom变量：Ccom变量

每个构造函数通过调用`CComVariant``VariantInit`Win32 函数或根据传递的参数设置对象的值和类型来处理对象的安全初始化。

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
[在]用于`CComVariant`初始化`CComVariant`对象的 或 VARIANT。 源变体的内容将复制到目标，无需转换。

*lpszSrc*<br/>
[在]用于初始化`CComVariant`对象的字符串。 您可以将零端端宽（Unicode）字符串传递给构造函数的 LPCOLESTR 版本，也可以将 ANSI 字符串传递给 LPCSTR 版本。 在这两种情况下，字符串都将转换为使用`SysAllocString`分配的 Unicode BSTR。 `CComVariant`对象的类型将VT_BSTR。

*bSrc*<br/>
[在]用于**bool**初始化`CComVariant`对象的布尔。 在存储之前 **，bool**参数将转换为VARIANT_BOOL。 `CComVariant`对象的类型将VT_BOOL。

*恩斯尔克*<br/>
[在]**int，** **BYTE，****短**，**长**， 龙， ULONGLONG，**无符号短**，**无符号长**， 或**无符号的 int**用于初始`CComVariant`化对象. `CComVariant`对象的类型将分别为VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4或VT_UI4。

*弗茨尔克*<br/>
[在]变体的类型。 当第一个参数为**int**时，有效类型VT_I4并VT_INT。 当第一个参数**长**时，有效类型VT_I4并VT_ERROR。 当第一个参数**为双精度**时，有效类型VT_R8，并VT_DATE。 当第一个参数**为无符号 int**时，有效类型VT_UI4和VT_UINT。

*fltSrc*<br/>
[在]用于初始化`CComVariant`对象的**浮点**。 `CComVariant`对象的类型将VT_R4。

*德布尔斯克*<br/>
[在]用于初始化`CComVariant`对象**的双精度值**。 `CComVariant`对象的类型将VT_R8。

*西斯尔克*<br/>
[在]`CY`用于初始化对象。 `CComVariant` `CComVariant`对象的类型将VT_CY。

*pSrc*<br/>
[在]用于`IDispatch`初始`IUnknown`化`CComVariant`对象的 或 指针。 `AddRef`将在接口指针上调用。 `CComVariant`对象的类型将分别VT_DISPATCH或VT_UNKNOWN。

或者，用于初始化`CComVariant`对象的 SAFERRAY 指针。 SAFEARRAY 的副本存储在对象中`CComVariant`。 `CComVariant`对象的类型将是 SAFEARRAY 的原始类型和VT_ARRAY的组合。

*证监会*<br/>
[在]用于**char**初始化`CComVariant`对象的字符。 `CComVariant`对象的类型将VT_I1。

*布斯特施尔*<br/>
[在]用于初始化`CComVariant`对象的 BSTR。 `CComVariant`对象的类型将VT_BSTR。

### <a name="remarks"></a>备注

析构函数通过调用[CComvariant：：：Clear](#clear)来管理清理。

## <a name="ccomvariantccomvariant"></a><a name="dtor"></a>CCom变量：*Ccom变量

析构函数。

```
~CComVariant() throw();
```

### <a name="remarks"></a>备注

此方法通过调用[CComvariant：：：Clear](#clear)来管理清理。

## <a name="ccomvariantchangetype"></a><a name="changetype"></a>CCom 变量：更改类型

将`CComVariant`对象转换为新类型。

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>参数

*vtNew*<br/>
[在]`CComVariant`对象的新类型。

*pSrc*<br/>
[在]指向 VARIANT 的指针，其值将转换为新类型。 默认值为 NULL，这意味着`CComVariant`对象将就地转换。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

如果传递*pSrc*的值，`ChangeType`将使用此 VARIANT 作为转换的源。 否则，`CComVariant`对象将是源。

## <a name="ccomvariantclear"></a><a name="clear"></a>CCom 变量：清除

通过调用`CComVariant``VariantClear`Win32 函数清除对象。

```
HRESULT Clear();
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

析构函数自动调用`Clear`。

## <a name="ccomvariantcopy"></a><a name="copy"></a>CCom 变量：复制

释放对象，`CComVariant`然后分配给指定的 VARIANT 的副本。

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>参数

*pSrc*<br/>
[在]指向要复制[的 VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="ccomvariantcopyto"></a><a name="copyto"></a>Ccom 变量：：复制到

复制`CComVariant`对象的内容。

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>参数

*普斯特德斯特*<br/>
指向将收到`CComVariant`对象内容副本的 BSTR。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

对象`CComVariant`必须为VT_BSTR类型。

## <a name="ccomvariantdetach"></a><a name="detach"></a>CComVariant：:Detach

从`CComVariant`对象分离基础 VARIANT 并将对象的类型设置为VT_EMPTY。

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>参数

*pDest*<br/>
[出]返回对象的基础 VARIANT 值。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

请注意，在分配调用`CComVariant`对象的值和类型之前，将自动清除*pDest*引用的 VARIANT 的内容。

## <a name="ccomvariantgetsize"></a><a name="getsize"></a>CCom 变量：获取 Size

对于简单固定大小 VARIANTs，此方法返回基础数据类型**的大小**加上**大小（VARTYPE）。**

```
ULONG GetSize() const;
```

### <a name="return-value"></a>返回值

`CComVariant`对象当前内容的大小（以字节为单位）。

### <a name="remarks"></a>备注

如果 VARIANT 包含接口指针，则`GetSize`查询`IPersistStream`或`IPersistStreamInit`。 如果成功，则返回值是返回`GetSizeMax`的值的低阶 32 位，加上 CLSID**的大小**和大小 **（VARTYPE）。** 如果接口指针为 NULL，`GetSize`则返回 CLSID**的大小**加上 **（VARTYPE） 的大小**。 如果总大小大于ULONG_MAX，`GetSize`则返回表示错误的 **（VARTYPE） 大小**。

在所有其他情况下，从当前 VARIANT 强制使用VT_BSTR类型的临时 VARIANT。 此 BSTR 的长度计算为字符串的长度加上字符串本身的长度加上空字符的大小加上**大小（VARTYPE）。** 如果无法强制将 VARIANT 强制到类型VT_BSTR的 VARIANT，则`GetSize`返回**大小（VARTYPE）。**

此方法返回的大小与[CComVariant：writeToStream](#writetostream)在成功条件下使用的字节数匹配。

## <a name="ccomvariantoperator-"></a><a name="operator_eq"></a>CComVariant：：运算符 |

为`CComVariant`对象分配值和相应的类型。

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
[在]要`CComVariant`分配给`CComVariant`对象的[或 变数](/windows/win32/api/oaidl/ns-oaidl-variant)。 源变体的内容将复制到目标，无需转换。

*布斯特施尔*<br/>
[在]要分配给`CComVariant`对象的 BSTR。 `CComVariant`对象的类型将VT_BSTR。

*lpszSrc*<br/>
[在]要分配给`CComVariant`对象的字符串。 您可以将零端接宽（Unicode）字符串传递给运算符的 LPCOLESTR 版本，将 ANSI 字符串传递给 LPCSTR 版本。 在这两种情况下，字符串都将转换为使用`SysAllocString`分配的 Unicode BSTR。 `CComVariant`对象的类型将VT_BSTR。

*bSrc*<br/>
[在]要**bool**分配给`CComVariant`对象的布尔。 在存储之前 **，bool**参数将转换为VARIANT_BOOL。 `CComVariant`对象的类型将VT_BOOL。

*恩斯尔克*<br/>
[在]**int、** BYTE、**短**、**长**、 龙、 ULONGLONG、**未签名短**、**无符号长**或**未签名的 int**分配给`CComVariant`对象。 `CComVariant`对象的类型将分别为VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4或VT_UI4。

*fltSrc*<br/>
[在]要分配给`CComVariant`对象的**float。** `CComVariant`对象的类型将VT_R4。

*德布尔斯克*<br/>
[在]要分配给`CComVariant`对象的**Double。** `CComVariant`对象的类型将VT_R8。

*西斯尔克*<br/>
[在]`CY`要分配给对象。 `CComVariant` `CComVariant`对象的类型将VT_CY。

*pSrc*<br/>
[在]要`IDispatch`分配给`IUnknown``CComVariant`对象的 或指针。 `AddRef`将在接口指针上调用。 `CComVariant`对象的类型将分别VT_DISPATCH或VT_UNKNOWN。

或者，要分配给`CComVariant`对象的 SAFEARRAY 指针。 SAFEARRAY 的副本存储在对象中`CComVariant`。 `CComVariant`对象的类型将是 SAFEARRAY 的原始类型和VT_ARRAY的组合。

*证监会*<br/>
[在]要分配给`CComVariant`对象的字符。 `CComVariant`对象的类型将VT_I1。

## <a name="ccomvariantoperator-"></a><a name="operator_eq_eq"></a>CComVariant：：运算符 |

指示`CComVariant`对象是否等于指定的 VARIANT。

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果*varSrc*的值和类型分别等于`CComVariant`对象的值和类型，则返回 TRUE。 否则为 FALSE。 操作员使用用户的默认区域设置执行比较。

运算符仅比较变体类型的值。 它比较字符串、整数和浮点，但不比较数组或记录。

## <a name="ccomvariantoperator-"></a><a name="operator_neq"></a>CComVariant：：操作员！*

指示`CComVariant`对象是否等于指定的 VARIANT。

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果*varSrc*的值或类型不分别等于`CComVariant`对象的值或类型，则返回 TRUE。 否则为 FALSE。 操作员使用用户的默认区域设置执行比较。

运算符仅比较变体类型的值。 它比较字符串、整数和浮点，但不比较数组或记录。

## <a name="ccomvariantoperator-lt"></a><a name="operator_lt"></a>CCom变量：：运算符&lt;

指示`CComVariant`对象是否小于指定的 VARIANT。

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果`CComVariant`对象的值小于*varSrc*的值，则返回 TRUE。 否则为 FALSE。 操作员使用用户的默认区域设置执行比较。

## <a name="ccomvariantoperator-gt"></a><a name="operator_gt"></a>CCom变量：：运算符&gt;

指示`CComVariant`对象是否大于指定的 VARIANT。

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>备注

如果`CComVariant`对象的值大于*varSrc*的值，则返回 TRUE。 否则为 FALSE。 操作员使用用户的默认区域设置执行比较。

## <a name="ccomvariantreadfromstream"></a><a name="readfromstream"></a>Ccom 变量：：从流中读取

将基础 VARIANT 设置到指定流中包含的 VARIANT。

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>参数

*pStream*<br/>
[在]指向流中包含数据的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

`ReadToStream`需要之前调用[WriteToStream](#writetostream)。

## <a name="ccomvariantsetbyref"></a><a name="setbyref"></a>Ccom 变量：：设置ByRef

初始化对象并将`CComVariant``vt`成员设置为VT_BYREF。

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>参数

*T*<br/>
变量的类型，例如 BSTR、int**int**或**字符**。

*铂*<br/>
用于初始化`CComVariant`对象的指针。

### <a name="remarks"></a>备注

`SetByRef`是一个函数模板，用于将`CComVariant`对象初始化到指针*pT*并将`vt`成员设置到VT_BYREF。 例如：

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

## <a name="ccomvariantwritetostream"></a><a name="writetostream"></a>Ccom 变量：：写入流

将基础 VARIANT 保存到流中。

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>参数

*pStream*<br/>
[在]指向流上的[IStream](/windows/win32/api/objidl/nn-objidl-istream)接口的指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
