---
title: COleVariant 类
ms.date: 11/04/2016
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
ms.openlocfilehash: 63bce4695e4e1142b797f24cfbbae71638177d04
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470896"
---
# <a name="colevariant-class"></a>COleVariant 类

封装 [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) 数据类型。

## <a name="syntax"></a>语法

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[COleVariant：： COleVariant](#colevariant)|构造 `COleVariant` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[COleVariant：： Attach](#attach)|将变体附加到 `COleVariant` 。|
|[COleVariant：： ChangeType](#changetype)|更改此对象的变量类型 `COleVariant` 。|
|[COleVariant：： Clear](#clear)|清除此 `COleVariant` 对象。|
|[COleVariant：:D etach](#detach)|从分离变量 `COleVariant` 并返回变量。|
|[COleVariant：： GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|从现有变体数组中检索字节数组。|
|[COleVariant：： SetString](#setstring)|将字符串设置为特定类型，通常为 ANSI。|

### <a name="public-operators"></a>公共运算符

|“属性”|描述|
|----------|-----------------|
|[COleVariant：： operator LPCVARIANT](#operator_lpcvariant)|将 `COleVariant` 值转换为 `LPCVARIANT` 。|
|[COleVariant：： operator LPVARIANT](#operator_lpvariant)|将 `COleVariant` 对象转换为 `LPVARIANT` 。|
|[COleVariant：： operator =](#operator_eq)|复制 `COleVariant` 值。|
|[COleVariant：： operator = =](#operator_eq_eq)|比较两个 `COleVariant` 值。|
|[COleVariant：： operator &lt; &lt; ，&gt;&gt;](#operator_lt_lt__gt_gt)|`COleVariant`将值输出到 `CArchive` 或 `CDumpContext` ，并输入 `COleVariant` 中的对象 `CArchive` 。|

## <a name="remarks"></a>备注

此数据类型用于 OLE 自动化。 具体而言， [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)结构包含指向变体结构的数组的指针。 `DISPPARAMS`结构用于将参数传递到[IDispatch：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

> [!NOTE]
> 此类派生自 `VARIANT` 结构。 这意味着，可以 `COleVariant` 在调用的参数中传递 `VARIANT` ，该结构的数据成员可以 `VARIANT` 访问数据成员 `COleVariant` 。

这两个相关 MFC 类[COleCurrency](../../mfc/reference/colecurrency-class.md)和[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)封装 variant 数据类型 CURRENCY （ `VT_CY` ）和 DATE （ `VT_DATE` ）。 `COleVariant`类在 DAO 类中广泛使用; 有关此类的典型用法，请参阅这些类，例如[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

有关详细信息，请参阅 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)、 [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy-r1)、 [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)和[IDispatch：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)条目。

有关 `COleVariant` 类及其在 ole 自动化中的用法的详细信息，请参阅[自动化](../../mfc/automation.md)中的 "在 Ole 自动化中传递参数"。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="colevariantattach"></a><a name="attach"></a>COleVariant：： Attach

调用此函数可将给定的[变体](/windows/win32/api/oaidl/ns-oaidl-variant)对象附加到当前 `COleVariant` 对象。

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>参数

*varSrc*<br/>
`VARIANT`要附加到当前对象的现有对象 `COleVariant` 。

### <a name="remarks"></a>备注

此函数将*varSrc*的 VARTYPE 设置为 VT_EMPTY。

有关详细信息，请参阅 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)和[VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)项。

## <a name="colevariantcolevariant"></a><a name="colevariant"></a>COleVariant：： COleVariant

构造 `COleVariant` 对象。

```
COleVariant();
COleVariant(const VARIANT& varSrc);
COleVariant(const COleVariant& varSrc);
COleVariant(LPCVARIANT pSrc);
COleVariant(LPCTSTR lpszSrc);
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc);
COleVariant(CString& strSrc);
COleVariant(BYTE nSrc);
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2);
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4);
COleVariant(const COleCurrency& curSrc);
COleVariant(float fltSrc);
COleVariant(double dblSrc);
COleVariant(const COleDateTime& timeSrc);
COleVariant(const CByteArray& arrSrc);
COleVariant(const CLongBinary& lbSrc);
COleVariant(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>参数

*varSrc*<br/>
`COleVariant` `VARIANT` 要复制到新对象的现有或对象 `COleVariant` 。

*.Psrc*<br/>
指向 `VARIANT` 对象的指针，该对象将被复制到新的 `COleVariant` 对象中。

*lpszSrc*<br/>
要复制到新对象中的以 null 值结束的字符串 `COleVariant` 。

*vtSrc*<br/>
`VARTYPE`新 `COleVariant` 对象的。

*strSrc*<br/>
要复制到新对象中的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象 `COleVariant` 。

*nSrc*， *lSrc*要复制到新对象中的数字值 `COleVariant` 。

*vtSrc*<br/>
`VARTYPE`新 `COleVariant` 对象的。

*curSrc*<br/>
要复制到新对象中的[COleCurrency](../../mfc/reference/colecurrency-class.md)对象 `COleVariant` 。

*fltSrc*、 *dblSrc*<br/>
要复制到新的 `COleVariant` 对象中的数值。

*timeSrc*<br/>
要复制到新对象中的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象 `COleVariant` 。

*arrSrc*<br/>
要复制到新对象中的[CByteArray](../../mfc/reference/cbytearray-class.md)对象 `COleVariant` 。

*lbSrc*<br/>
要复制到新对象中的[CLongBinary](../../mfc/reference/clongbinary-class.md)对象 `COleVariant` 。

*pidl*<br/>
指向要复制到新对象中的[ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist)结构的指针 `COleVariant` 。

### <a name="remarks"></a>备注

所有这些构造函数 `COleVariant` 将创建初始化为指定值的新对象。 下面是每个构造函数的简要说明。

- **COleVariant （）** VT_EMPTY 创建一个空的 `COleVariant` 对象。

- **COleVariant （** *varSrc* **）** 复制现有的 `VARIANT` 或 `COleVariant` 对象。 变体类型将保留。

- **COleVariant （** *.psrc* **）** 复制现有的 `VARIANT` 或 `COleVariant` 对象。 变体类型将保留。

- **COleVariant （** *lpszSrc* **）** 将字符串复制到新的对象中，VT_BSTR （UNICODE）。

- **COleVariant （** *lpszSrc* **，** *vtSrc* **）** 将字符串复制到新的对象。 参数*vtSrc*必须 VT_BSTR （UNICODE）或 VT_BSTRT （ANSI）。

- **COleVariant （** *strSrc* **）** 将字符串复制到新的对象中，VT_BSTR （UNICODE）。

- **COleVariant （** *nSrc* **）** 将一个8位整数复制到新的对象中，VT_UI1。

- **COleVariant （** *nSrc* **，** *vtSrc* **）** 将一个16位整数（或布尔值）复制到新的对象。 参数*vtSrc*必须 VT_I2 或 VT_BOOL。

- **COleVariant （** *lSrc* **，** *vtSrc* **）** 将32位整数（或 SCODE 值）复制到新的对象。 参数*vtSrc*必须为 VT_I4、VT_ERROR 或 VT_BOOL。

- **COleVariant （** *curSrc* **）** 将 `COleCurrency` 值复制到新的对象中，VT_CY。

- **COleVariant （** *fltSrc* **）** 将32位浮点值复制到新的对象中，VT_R4。

- **COleVariant （** *dblSrc* **）** 将64位浮点值复制到新的对象中，VT_R8。

- **COleVariant （** *timeSrc* **）** 将 `COleDateTime` 值复制到新的对象中，VT_DATE。

- **COleVariant （** *arrSrc* **）** 将 `CByteArray` 对象复制到新的对象中，VT_EMPTY。

- **COleVariant （** *lbSrc* **）** 将 `CLongBinary` 对象复制到新的对象中，VT_EMPTY。

有关 SCODE 的详细信息，请参阅 Windows SDK 中[COM 错误代码的结构](/windows/win32/com/structure-of-com-error-codes)。

## <a name="colevariantchangetype"></a><a name="changetype"></a>COleVariant：： ChangeType

转换此对象中的变量值的类型 `COleVariant` 。

```cpp
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>参数

*vartype*<br/>
此对象的 VARTYPE `COleVariant` 。

*.Psrc*<br/>
指向要转换的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)对象的指针。 如果此值为 NULL，则 `COleVariant` 将此对象用作转换的源。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)、 [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)和[VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype)条目。

## <a name="colevariantclear"></a><a name="clear"></a>COleVariant：： Clear

清除 `VARIANT`。

```cpp
void Clear();
```

### <a name="remarks"></a>备注

这会将此对象的 VARTYPE 设置为 VT_EMPTY。 `COleVariant`析构函数调用此函数。

有关详细信息，请参阅 `VARIANT` Windows SDK 中的、VARTYPE 和 `VariantClear` 条目。

## <a name="colevariantdetach"></a><a name="detach"></a>COleVariant：:D etach

从此对象分离基础[变体](/windows/win32/api/oaidl/ns-oaidl-variant)对象 `COleVariant` 。

```
VARIANT Detach();
```

### <a name="remarks"></a>备注

此函数将此对象的 VARTYPE 设置 `COleVariant` 为 VT_EMPTY。

> [!NOTE]
> 调用后 `Detach` ，调用方负责调用 `VariantClear` 生成的 `VARIANT` 结构。

有关详细信息，请参阅 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)、 [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)和[VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)条目。

## <a name="colevariantgetbytearrayfromvariantarray"></a><a name="getbytearrayfromvariantarray"></a>COleVariant：： GetByteArrayFromVariantArray

从现有的变体数组中检索字节数组

```cpp
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>参数

*字节*<br/>
对现有[CByteArray](../../mfc/reference/cbytearray-class.md)对象的引用。

## <a name="colevariantoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleVariant：： operator LPCVARIANT

此强制转换运算符返回一个 `VARIANT` 结构，其值从此 `COleVariant` 对象复制。

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>备注

## <a name="colevariantoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleVariant：： operator LPVARIANT

调用此强制转换运算符可访问 `VARIANT` 此对象的基础结构 `COleVariant` 。

```
operator LPVARIANT();
```

### <a name="remarks"></a>备注

> [!CAUTION]
> 更改 `VARIANT` 此函数所返回的指针所访问的结构中的值将更改此对象的值 `COleVariant` 。

## <a name="colevariantoperator-"></a><a name="operator_eq"></a>COleVariant：： operator =

这些重载赋值运算符将源值复制到此 `COleVariant` 对象中。

```
const COleVariant& operator=(const VARIANT& varSrc);
const COleVariant& operator=(LPCVARIANT pSrc);
const COleVariant& operator=(const COleVariant& varSrc);
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc);
const COleVariant& operator=(BYTE nSrc);
const COleVariant& operator=(short nSrc);
const COleVariant& operator=(long lSrc);
const COleVariant& operator=(const COleCurrency& curSrc);
const COleVariant& operator=(float fltSrc);
const COleVariant& operator=(double dblSrc);
const COleVariant& operator=(const COleDateTime& dateSrc);
const COleVariant& operator=(const CByteArray& arrSrc);
const COleVariant& operator=(const CLongBinary& lbSrc);
```

### <a name="remarks"></a>备注

下面是每个运算符的简要说明：

- **operator = （** *varSrc* **）** 将现有的变体或 `COleVariant` 对象复制到此对象中。

- **operator = （** *.psrc* **）** 将 *.psrc*访问的变量对象复制到此对象中。

- **operator = （** *lpszSrc* **）** 将以 null 结尾的字符串复制到此对象中，并将 VARTYPE 设置为 VT_BSTR。

- **operator = （** *strSrc* **）** 将[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象复制到此对象中，并将 VARTYPE 设置为 VT_BSTR。

- **operator = （** *nSrc* **）** 将一个8位或16位整数值复制到此对象中。 如果*nSrc*是一个8位值，则将此的 VARTYPE 设置为 VT_UI1。 如果*nSrc*是一个16位值，并且 VT_BOOL 的 VARTYPE，则会保留该值;否则，将其设置为 VT_I2。

- **operator = （** *lSrc* **）** 将32位整数值复制到此对象中。 如果这是 VT_ERROR 的 VARTYPE，则将其保留;否则，将其设置为 VT_I4。

- **operator = （** *curSrc* **）** 将[COleCurrency](../../mfc/reference/colecurrency-class.md)对象复制到此对象中，并将 VARTYPE 设置为 VT_CY。

- **operator = （** *fltSrc* **）** 将32位浮点值复制到此对象中，并将 VARTYPE 设置为 VT_R4。

- **operator = （** *dblSrc* **）** 将64位浮点值复制到此对象中，并将 VARTYPE 设置为 VT_R8。

- **operator = （** *dateSrc* **）** 将[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象复制到此对象中，并将 VARTYPE 设置为 VT_DATE。

- **operator = （** *arrSrc* **）** 将[CByteArray](../../mfc/reference/cbytearray-class.md)对象复制到此 `COleVariant` 对象中。

- **operator = （** *lbSrc* **）** 将[CLongBinary](../../mfc/reference/clongbinary-class.md)对象复制到此 `COleVariant` 对象中。

有关详细信息，请参阅 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)和[VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)项。

## <a name="colevariantoperator-"></a><a name="operator_eq_eq"></a>COleVariant：： operator = =

此运算符比较两个变体值，如果相等，则返回非零值;否则为0。

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

## <a name="colevariantoperator-ltlt-gtgt"></a><a name="operator_lt_lt__gt_gt"></a>COleVariant：： operator &lt; &lt; ，&gt;&gt;

`COleVariant`将值输出到 `CArchive` 或 `CdumpContext` ，并输入 `COleVariant` 中的对象 `CArchive` 。

```
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    OleVariant varSrc);

friend CArchive& AFXAPI operator<<(
    CArchive& ar,
    COleVariant varSrc);

friend CArchive& AFXAPI operator>>(
    CArchive& ar,
    COleVariant& varSrc);
```

### <a name="remarks"></a>备注

`COleVariant`插入（ **\<\<**) operator supports diagnostic dumping and storing to an archive. The extraction (**>>** ）运算符支持从存档中加载。

## <a name="colevariantsetstring"></a><a name="setstring"></a>COleVariant：： SetString

将字符串设置为特定类型。

```cpp
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>参数

*lpszSrc*<br/>
要复制到新对象中的以 null 值结束的字符串 `COleVariant` 。

*VtSrc*<br/>
新对象的 VARTYPE `COleVariant` 。

### <a name="remarks"></a>备注

参数*vtSrc*必须 VT_BSTR （UNICODE）或 VT_BSTRT （ANSI）。 `SetString`通常用于将字符串设置为 ANSI，因为使用字符串或字符串指针参数的[COleVariant：： COleVariant](#colevariant)构造函数的默认值，且不能是 UNICODE。

非 UNICODE 生成中的 DAO 记录集需要字符串为 ANSI。 因此，对于使用对象的 DAO `COleVariant` 函数，如果不创建 UNICODE 记录集，则必须使用构造函数的**COleVariant：： COleVariant （** *lpszSrc* **，** *vtSrc* **）** 形式，将*vtSrc*设置为 VT_BSTRT （ANSI），或将 vtSrc 设置 `SetString` 为 VT_BSTRT 以生成 ANSI 字符串。 *vtSrc* 例如， `CDaoRecordset` 函数[CDaoRecordset：： Seek](../../mfc/reference/cdaorecordset-class.md#seek)和[CDaoRecordset：： SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue)将 `COleVariant` 对象用作参数。 如果 DAO 记录集不是 UNICODE，则这些对象必须为 ANSI。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
