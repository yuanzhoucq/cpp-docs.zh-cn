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
ms.openlocfilehash: f907ed7c058f87cf03530411bc8fa4a3c108a4f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374823"
---
# <a name="colevariant-class"></a>COleVariant 类

封装 [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) 数据类型。

## <a name="syntax"></a>语法

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle变量：COle变量](#colevariant)|构造 `COleVariant` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle 变量：附加](#attach)|将 VARIANT 附加到`COleVariant`。|
|[COle 变量：更改类型](#changetype)|更改此`COleVariant`对象的变体类型。|
|[COle 变量：清除](#clear)|清除此 `COleVariant` 对象。|
|[COleVariant：:D](#detach)|从 分离 VARIANT`COleVariant`并从 中返回 VARIANT。|
|[COlevariant：从变量数组获取字节数组](#getbytearrayfromvariantarray)|从现有变体数组检索字节数组。|
|[COle 变量：：设置字符串](#setstring)|将字符串设置为特定类型，通常是 ANSI。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[COle变量：：运算符 LPCVARIANT](#operator_lpcvariant)|将`COleVariant`值转换为`LPCVARIANT`。|
|[COle变量：：运算符 LPVARIANT](#operator_lpvariant)|将`COleVariant`对象转换为`LPVARIANT`。|
|[COleVariant：：运算符 |](#operator_eq)|复制值`COleVariant`。|
|[COle变量：：运算符 |](#operator_eq_eq)|比较两`COleVariant`个值。|
|[COleVariant：运算符&lt;&lt;，&gt;&gt;](#operator_lt_lt__gt_gt)|将`COleVariant``CArchive`值输出到 或`CDumpContext`并从`COleVariant`中输入`CArchive`对象。|

## <a name="remarks"></a>备注

此数据类型用于 OLE 自动化。 具体而言[，DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)结构包含指向 VARIANT 结构数组的指针。 结构`DISPPARAMS`用于将参数传递给[IDispatch：：：invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

> [!NOTE]
> 此类派生自结构`VARIANT`。 这意味着您可以传递 调用`COleVariant`的`VARIANT`参数，并且`VARIANT`结构的数据成员是 可`COleVariant`访问的数据成员。

两个相关的 MFC 类[COleCurrency](../../mfc/reference/colecurrency-class.md)和[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)封装了`VT_CY`变体数据类型货币`VT_DATE`（ ） 和 DATE （ ）。 该`COleVariant`类在 DAO 类中广泛使用;有关此类的典型用法，请参阅这些类，例如[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

有关详细信息，请参阅[变体](/windows/win32/api/oaidl/ns-oaidl-variant)、[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)[、DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)和[IDispatch：调用](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)Windows SDK 中的条目。

有关`COleVariant`该类及其在 OLE 自动化中的使用的详细信息，请参阅文章["在](../../mfc/automation.md)OLE 自动化中传递参数"。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="colevariantattach"></a><a name="attach"></a>COle 变量：附加

调用此函数以将给定[的 VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)对象附加到`COleVariant`当前对象。

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>参数

*varSrc*<br/>
要附加到`VARIANT`当前`COleVariant`对象的现有对象。

### <a name="remarks"></a>备注

此函数将*varSrc*的 VARTYPE 设置为VT_EMPTY。

有关详细信息，请参阅 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)和[VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)条目。

## <a name="colevariantcolevariant"></a><a name="colevariant"></a>COle变量：COle变量

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
要复制到`COleVariant`新`VARIANT``COleVariant`对象的现有或对象。

*pSrc*<br/>
指向将复制到新`VARIANT``COleVariant`对象的对象的指针。

*lpszSrc*<br/>
要复制到新`COleVariant`对象的 null 终止字符串。

*弗茨尔克*<br/>
为新`VARTYPE``COleVariant`对象的 。

*斯特斯尔克*<br/>
要复制到新`COleVariant`对象的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象。

*nSrc，* *lSrc*要复制到新`COleVariant`对象的数值。

*弗茨尔克*<br/>
为新`VARTYPE``COleVariant`对象的 。

*库尔斯克*<br/>
要复制到新`COleVariant`对象的[COleCurrency](../../mfc/reference/colecurrency-class.md)对象。

*fltSrc*，*德布尔斯尔*<br/>
要复制到新的 `COleVariant` 对象中的数值。

*时间Src*<br/>
要复制到新`COleVariant`对象的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象。

*阿尔斯尔克*<br/>
要复制到新`COleVariant`对象的[CByteArray](../../mfc/reference/cbytearray-class.md)对象。

*磅斯尔*<br/>
要复制到新`COleVariant`对象的[CLongBinary](../../mfc/reference/clongbinary-class.md)对象。

*皮德尔*<br/>
指向要复制到新`COleVariant`对象的[ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist)结构的指针。

### <a name="remarks"></a>备注

所有这些构造函数都创建初始化`COleVariant`为指定值的新对象。 下面简要介绍了每个构造函数。

- **COleVariant）** 创建空`COleVariant`对象，VT_EMPTY。

- **COlevariant（** *varsrc* **）** 复制现有`VARIANT`对象或`COleVariant`对象。 变体类型将保留。

- **COlevariant（** *pSrc* **）** 复制现有`VARIANT`对象或`COleVariant`对象。 变体类型将保留。

- **COlevariant（** *lpszSrc* **）** 将字符串复制到新对象VT_BSTR （UNICODE）。

- **COlevariant（lpszSrc，** *lpszSrc* **,** *vtSrc* **）** 将字符串复制到新对象中。 参数*vtSrc*必须VT_BSTR （UNICODE） 或VT_BSTRT （ANSI）。

- **COlevariant（** *斯特斯克* **）** 将字符串复制到新对象VT_BSTR （UNICODE）。

- **COlevariant（** *nSrc* **）** 将 8 位整数复制到新对象，VT_UI1。

- **COlevariant（** *nSrc* **，** *vtSrc* **）** 将 16 位整数（或布尔值）复制到新对象中。 参数*vtSrc*必须VT_I2或VT_BOOL。

- **COlevariant（** *lSrc* **，** *vtSrc* **）** 将 32 位整数（或 SCODE 值）复制到新对象中。 参数*vtSrc*必须VT_I4、VT_ERROR 或VT_BOOL。

- **COlevariant（** *库尔斯rc* **）** 将`COleCurrency`值复制到新对象，VT_CY。

- **COlevariant（** *fltsrc* **）** 将 32 位浮点值复制到新对象，VT_R4。

- **COlevariant（** *dblSrc* **）** 将 64 位浮点值复制到新对象中，VT_R8。

- **COlevariant（** *时间 Src* **）** 将`COleDateTime`值复制到新对象VT_DATE。

- **COlevariant（** *arrSrc* **）** 将`CByteArray`对象复制到新对象，VT_EMPTY。

- **COlevariant（** *磅Src* **）** 将`CLongBinary`对象复制到新对象，VT_EMPTY。

有关 SCODE 的详细信息，请参阅 Windows SDK 中的[COM 错误代码结构](/windows/win32/com/structure-of-com-error-codes)。

## <a name="colevariantchangetype"></a><a name="changetype"></a>COle 变量：更改类型

转换此`COleVariant`对象中的变体值的类型。

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>参数

*vartype*<br/>
此`COleVariant`对象的 VARTYPE。

*pSrc*<br/>
指向要转换[的 VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)对象的指针。 如果此值为 NULL，则`COleVariant`此对象用作转换的源。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)SDK 中的[VARIANT、VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)和[变体更改类型](/windows/win32/api/oleauto/nf-oleauto-variantchangetype)条目。

## <a name="colevariantclear"></a><a name="clear"></a>COle 变量：清除

清除 `VARIANT`。

```
void Clear();
```

### <a name="remarks"></a>备注

这将为此对象的 VARTYPE 设置为VT_EMPTY。 析`COleVariant`构函数调用此函数。

有关详细信息，请参阅 Windows `VARIANT`SDK 中的 VARTYPE 和`VariantClear`条目。

## <a name="colevariantdetach"></a><a name="detach"></a>COleVariant：:D

从该`COleVariant`对象分离基础[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)对象。

```
VARIANT Detach();
```

### <a name="remarks"></a>备注

此函数为此`COleVariant`对象的 VARTYPE 设置为VT_EMPTY。

> [!NOTE]
> 调用`Detach`后，调用者负责调用`VariantClear`生成的`VARIANT`结构。

有关详细信息，请参阅 Windows [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)SDK 中的[VARIANT、VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)和[变体清除](/windows/win32/api/oleauto/nf-oleauto-variantclear)条目。

## <a name="colevariantgetbytearrayfromvariantarray"></a><a name="getbytearrayfromvariantarray"></a>COlevariant：从变量数组获取字节数组

从现有变体数组检索字节数组

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>参数

*字节*<br/>
对现有[CByteArray](../../mfc/reference/cbytearray-class.md)对象的引用。

## <a name="colevariantoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COle变量：：运算符 LPCVARIANT

此强制转换运算符返回`VARIANT`其值从此`COleVariant`对象复制的结构。

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>备注

## <a name="colevariantoperator-lpvariant"></a><a name="operator_lpvariant"></a>COle变量：：运算符 LPVARIANT

调用此强制转换运算符以访问此`VARIANT``COleVariant`对象的基础结构。

```
operator LPVARIANT();
```

### <a name="remarks"></a>备注

> [!CAUTION]
> 更改此函数返回的`VARIANT`指针访问的结构中的值将更改此`COleVariant`对象的值。

## <a name="colevariantoperator-"></a><a name="operator_eq"></a>COleVariant：：运算符 |

这些重载赋值运算符将源值复制到此`COleVariant`对象中。

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

每个运算符的简要描述如下：

- 运算符 **（varSrc* **operator =(** **）** 将现有的 VARIANT`COleVariant`或对象复制到此对象中。

- 运算符 *=（pSrc* **operator =(** **）** 将*pSrc*访问的 VARIANT 对象复制到此对象中。

- 运算符 *=（lpszSrc* **）** **operator =(** 将 null 终止的字符串复制到此对象，并将 VARTYPE 设置到VT_BSTR。

- 运算符 *=（strSrc* **operator =(** **）** 将[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象复制到此对象，并将 VARTYPE 设置到VT_BSTR。

- 运算符 **（nSrc）* **)** **operator =(** 将 8 位或 16 位整数值复制到此对象中。 如果*nSrc*是 8 位值，则此值的 VARTYPE 设置为VT_UI1。 如果*nSrc*是 16 位值，并且其 VARTYPE 是VT_BOOL，则保留该值;否则，它将设置为VT_I2。

- 运算符 *=（lSrc* **operator =(** **）** 将 32 位整数值复制到此对象中。 如果VT_ERROR，则保留它;否则，它将设置为VT_I4。

- 运算符 **（curSrc* **operator =(** **）** 将[COleCurrency](../../mfc/reference/colecurrency-class.md)对象复制到此对象，并将 VARTYPE 设置到VT_CY。

- 运算符 *=（fltSrc）* **)** **operator =(** 将 32 位浮点值复制到此对象，并将 VARTYPE 设置为VT_R4。

- 运算符 *=（dblSrc）* **)** **operator =(** 将 64 位浮点值复制到此对象，并将 VARTYPE 设置到VT_R8。

- **操作员 *（***日期Src）* **)** 将[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象复制到此对象，并将 VARTYPE 设置到VT_DATE。

- 运算符 *=（arrSrc）* **)** **operator =(** 将[CByteArray](../../mfc/reference/cbytearray-class.md)对象复制到`COleVariant`此对象。

- **操作员 *（***磅Src）* **)** 将[CLongBinary](../../mfc/reference/clongbinary-class.md)对象复制到`COleVariant`此对象。

有关详细信息，请参阅 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)和[VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)条目。

## <a name="colevariantoperator-"></a><a name="operator_eq_eq"></a>COle变量：：运算符 |

此运算符比较两个变体值，如果它们相等，则返回非零;否则 0。

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

## <a name="colevariantoperator-ltlt-gtgt"></a><a name="operator_lt_lt__gt_gt"></a>COleVariant：运算符&lt;&lt;，&gt;&gt;

将`COleVariant``CArchive`值输出到 或`CdumpContext`并从`COleVariant`中输入`CArchive`对象。

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

插入`COleVariant`（**\<**） 运算符支持诊断转储并存储到存档。 提取 （**>>**） 运算符支持从存档加载。

## <a name="colevariantsetstring"></a><a name="setstring"></a>COle 变量：：设置字符串

将字符串设置为特定类型。

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>参数

*lpszSrc*<br/>
要复制到新`COleVariant`对象的 null 终止字符串。

*VtSrc*<br/>
新`COleVariant`对象的 VARTYPE。

### <a name="remarks"></a>备注

参数*vtSrc*必须VT_BSTR （UNICODE） 或VT_BSTRT （ANSI）。 `SetString`通常用于将字符串设置为 ANSI，因为[COleVariant：：COleVariant](#colevariant)构造函数的默认值带有字符串或字符串指针参数，并且没有 VARTYPE 是 UNICODE。

非 UNICODE 生成中的 DAO 记录集希望字符串为 ANSI。 因此，`COleVariant`对于使用对象的 DAO 函数，如果不创建 UNICODE 记录集，则必须使用**COleVariant：：COleVariant（lpszSrc、vtSrc）***lpszSrc***,***vtSrc***)** 形式的构造函数 *，vtSrc*设置为VT_BSTRT （ANSI），或者与设置为`SetString`VT_BSTRT的*vtSrc*一起生成 ANSI 字符串。 例如，`CDaoRecordset`函数[CDaoRecordset：：seek](../../mfc/reference/cdaorecordset-class.md#seek)和[CDaoRecordset：setFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) `COleVariant`使用对象作为参数。 如果 DAO 记录集不是 UNICODE，则这些对象必须是 ANSI。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
