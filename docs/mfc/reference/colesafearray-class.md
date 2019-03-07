---
title: COleSafeArray 类
ms.date: 08/27/2018
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
ms.openlocfilehash: 0833dca9311689063c2ebeadd3942d9f5ce376e2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267155"
---
# <a name="colesafearray-class"></a>COleSafeArray 类

与任意类型和维度的数组一起使用的类。

## <a name="syntax"></a>语法

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|构造 `COleSafeArray` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|检索指向数组数据的指针。|
|[COleSafeArray::AllocData](#allocdata)|为数组分配内存。|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|为安全数组描述符分配内存。|
|[COleSafeArray::Attach](#attach)|使控制现有`VARIANT`数组到`COleSafeArray`对象。|
|[COleSafeArray::Clear](#clear)|释放基础中的所有数据`VARIANT`。|
|[COleSafeArray::Copy](#copy)|创建现有数组的副本。|
|[COleSafeArray::Create](#create)|创建安全数组。|
|[COleSafeArray::CreateOneDim](#createonedim)|创建一维`COleSafeArray`对象。|
|[COleSafeArray::Destroy](#destroy)|销毁现有数组。|
|[COleSafeArray::DestroyData](#destroydata)|销毁安全数组中的数据。|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|销毁安全数组描述符。|
|[COleSafeArray::Detach](#detach)|分离的变体数组从`COleSafeArray`对象 （以便不会释放数据）。|
|[COleSafeArray::GetByteArray](#getbytearray)|将复制到安全数组的内容[CByteArray](../../mfc/reference/cbytearray-class.md)。|
|[COleSafeArray::GetDim](#getdim)|返回数组中的维数。|
|[COleSafeArray::GetElement](#getelement)|检索单个元素的安全数组。|
|[COleSafeArray::GetElemSize](#getelemsize)|返回的大小，以字节为单位的安全数组中的一个元素。|
|[COleSafeArray::GetLBound](#getlbound)|返回安全数组任意维度的下限。|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|返回的元素数中的一维`COleSafeArray`对象。|
|[COleSafeArray::GetUBound](#getubound)|返回安全数组任意维度的上限。|
|[COleSafeArray::Lock](#lock)|数组的锁计数递增并放置在数组描述符的指向数组数据的指针。|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|返回指向已索引元素的指针。|
|[COleSafeArray::PutElement](#putelement)|将单个元素分配到数组。|
|[COleSafeArray::Redim](#redim)|更改安全数组的最低有效 （最右边） 绑定。|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|一维中的元素数更改`COleSafeArray`对象。|
|[COleSafeArray::UnaccessData](#unaccessdata)|递减锁计数数组，使无效指针来检索`AccessData`。|
|[COleSafeArray::Unlock](#unlock)|减少锁计数的一个数组，因此它可以释放或调整大小。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|访问基础`VARIANT`结构的`COleSafeArray`对象。|
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|访问基础`VARIANT`结构的`COleSafeArray`对象。|
|[COleSafeArray::operator =](#operator_eq)|将复制到的值`COleSafeArray`对象 (`SAFEARRAY`， `VARIANT`， `COleVariant`，或`COleSafeArray`数组)。|
|[COleSafeArray::operator ==](#operator_eq_eq)|比较两个变体的数组 (`SAFEARRAY`， `VARIANT`， `COleVariant`，或`COleSafeArray`数组)。|
|[COleSafeArray::operator &lt;&lt;](#operator_lt_lt)|输出的内容`COleSafeArray`转储上下文的对象。|

## <a name="remarks"></a>备注

`COleSafeArray` 派生自 OLE`VARIANT`结构。 OLE`SAFEARRAY`成员函数是可通过`COleSafeArray`，同时为一系列专为一维字节数组的成员函数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

##  <a name="accessdata"></a>  COleSafeArray::AccessData

检索指向数组数据的指针。

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>参数

*ppvData*<br/>
指向数组数据的指针指向的指针。

### <a name="remarks"></a>备注

出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

##  <a name="allocdata"></a>  COleSafeArray::AllocData

为安全数组分配内存。

```
void AllocData();
```

### <a name="remarks"></a>备注

出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="allocdescriptor"></a>  COleSafeArray::AllocDescriptor

安全数组描述符分配内存。

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>参数

*dwDims*<br/>
安全数组中的维度数。

### <a name="remarks"></a>备注

出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="attach"></a>  COleSafeArray::Attach

中的现有数据的控制权`VARIANT`数组到`COleSafeArray`对象。

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>参数

*varSrc*<br/>
一个 `VARIANT` 对象。 *VarSrc*参数必须具有 VARTYPE [VT_ARRAY](/windows/desktop/api/wtypes/ne-wtypes-varenum)。

### <a name="remarks"></a>备注

源`VARIANT`的类型设置为 VT_EMPTY。 如果有，此函数将清除当前数组数据。

### <a name="example"></a>示例

  有关示例，请参阅[COleSafeArray::AccessData](#accessdata)。

##  <a name="clear"></a>  COleSafeArray::Clear

清除安全数组。

```
void Clear();
```

### <a name="remarks"></a>备注

该函数通过设置清除安全数组`VARTYPE`VT_EMPTY 于的对象。 当前内容将释放，并且该数组将被释放。

##  <a name="colesafearray"></a>  COleSafeArray::COleSafeArray

构造 `COleSafeArray` 对象。

```
COleSafeArray();

COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);

COleSafeArray(const COleSafeArray& saSrc);
COleSafeArray(const VARIANT& varSrc);
  COleSafeArray(LPCVARIANT pSrc);
COleSafeArray(const COleVariant& varSrc);
```

### <a name="parameters"></a>参数

*saSrc*<br/>
将现有`COleSafeArray`对象或`SAFEARRAY`若要复制到新`COleSafeArray`对象。

*vtSrc*<br/>
新的 VARTYPE`COleSafeArray`对象。

*psaSrc*<br/>
一个指向`SAFEARRAY`要复制到新`COleSafeArray`对象。

*varSrc*<br/>
将现有`VARIANT`或`COleVariant`要复制到新对象`COleSafeArray`对象。

*pSrc*<br/>
一个指向`VARIANT`对象复制到新`COleSafeArray`对象。

### <a name="remarks"></a>备注

所有这些构造函数创建新`COleSafeArray`对象。 如果没有参数，一个空`COleSafeArray`(VT_EMPTY) 创建对象。 如果`COleSafeArray`从其 VARTYPE 称为隐式的另一个数组复制 ( `COleSafeArray`， `COleVariant`，或`VARIANT`)，源数组的 VARTYPE 仍将保留，无需指定。 如果`COleSafeArray`从其 VARTYPE 未知的另一个数组复制 (`SAFEARRAY`)，必须在指定的 VARTYPE *vtSrc*参数。

出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="copy"></a>  COleSafeArray::Copy

创建现有安全数组的副本。

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>参数

*ppsa*<br/>
指向用于返回新数组描述符的位置。

### <a name="remarks"></a>备注

出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="create"></a>  COleSafeArray::Create

分配并初始化数组的数据。

```
void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    DWORD* rgElements);

void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    SAFEARRAYBOUND* rgsabounds);
```

### <a name="parameters"></a>参数

*vtSrc*<br/>
数组 (即，数组的每个元素的 VARTYPE) 基类型。 VARTYPE 被限制为变体类型的子集。 可以设置的 VT_BYREF 标志既 VT_ARRAY。 VT_EMPTY 和 VT_NULL 不是有效的数组的基类型。 所有其他类型是合法的。

*dwDims*<br/>
数组中的维度数。 之后创建数组时，可以更改此[Redim](#redim)。

*rgElements*<br/>
指向数组的元素数组中每个维度的数目。

*rgsabounds*<br/>
向量的边界 （一个用于每个维度） 的指针为数组分配。

### <a name="remarks"></a>备注

如有必要，此函数将清除当前的数组数据。 出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="createonedim"></a>  COleSafeArray::CreateOneDim

创建一个新一维`COleSafeArray`对象。

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>参数

*vtSrc*<br/>
数组 (即，数组的每个元素的 VARTYPE) 基类型。

*dwElements*<br/>
数组中的元素数。 之后创建数组时，可以更改此[ResizeOneDim](#resizeonedim)。

*pvSrcData*<br/>
指向要复制到数组的数据。

*nLBound*<br/>
数组的下限。

### <a name="remarks"></a>备注

该函数分配并初始化数组，如果复制指定的数据的数据指针*pvSrcData*不为 NULL。

出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

##  <a name="destroy"></a>  COleSafeArray::Destroy

销毁现有数组描述符和数组中的所有数据。

```
void Destroy();
```

### <a name="remarks"></a>备注

如果对象存储在数组中，每个对象被释放。 出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="destroydata"></a>  COleSafeArray::DestroyData

销毁安全数组中的所有数据。

```
void DestroyData();
```

### <a name="remarks"></a>备注

如果对象存储在数组中，每个对象被释放。 出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="destroydescriptor"></a>  COleSafeArray::DestroyDescriptor

销毁安全数组描述符。

```
void DestroyDescriptor();
```

### <a name="remarks"></a>备注

出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="detach"></a>  COleSafeArray::Detach

分离`VARIANT`中的数据`COleSafeArray`对象。

```
VARIANT Detach();
```

### <a name="return-value"></a>返回值

基础`VARIANT`中的值`COleSafeArray`对象。

### <a name="remarks"></a>备注

该函数通过将对象的 VARTYPE 设置为 VT_EMPTY 分离的安全数组中的数据。 它是调用方负责通过调用 Windows 函数来释放数组[VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear)。

出现错误时，该函数将引发[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

  有关示例，请参阅[COleSafeArray::PutElement](#putelement)。

##  <a name="getbytearray"></a>  COleSafeArray::GetByteArray

将复制到安全数组的内容`CByteArray`。

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>参数

*bytes*<br/>
对引用[CByteArray](../../mfc/reference/cbytearray-class.md)对象。

##  <a name="getdim"></a>  COleSafeArray::GetDim

返回中的维度数目`COleSafeArray`对象。

```
DWORD GetDim();
```

### <a name="return-value"></a>返回值

安全数组中的维度数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="getelement"></a>  Colesafearray:: Getelement

检索单个元素的安全数组。

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>参数

*rgIndices*<br/>
指向数组的每个维度的索引数组的指针。

*pvData*<br/>
指向要放置该数组的元素的位置。

### <a name="remarks"></a>备注

此函数将自动调用 windows 函数`SafeArrayLock`和`SafeArrayUnlock`之前和之后检索元素。 如果数据元素是字符串、 对象或变量，函数将元素复制正确的方式。 将参数*pvData*应指向一个大足够的缓冲区来包含该元素。

出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

##  <a name="getelemsize"></a>  COleSafeArray::GetElemSize

检索中的元素的大小`COleSafeArray`对象。

```
DWORD GetElemSize();
```

### <a name="return-value"></a>返回值

以字节为单位，安全数组的元素的大小。

##  <a name="getlbound"></a>  COleSafeArray::GetLBound

返回的任何维度的下限`COleSafeArray`对象。

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>参数

*dwDim*<br/>
要为其获取下限数组维度。

*pLBound*<br/>
指向要返回更低绑定的位置。

### <a name="remarks"></a>备注

出现错误时，该函数将引发[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

##  <a name="getonedimsize"></a>  COleSafeArray::GetOneDimSize

返回的元素数中的一维`COleSafeArray`对象。

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>返回值

一维的安全数组中的元素数。

### <a name="example"></a>示例

  有关示例，请参阅[COleSafeArray::CreateOneDim](#createonedim)。

##  <a name="getubound"></a>  COleSafeArray::GetUBound

返回安全数组任意维度的上限。

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>参数

*dwDim*<br/>
要为其获取上限数组维度。

*pUBound*<br/>
指向要返回上界的位置。

### <a name="remarks"></a>备注

出现错误时，该函数将引发[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

##  <a name="lock"></a>  COleSafeArray::Lock

数组和数组描述符中的数组数据的指针的位置的锁计数递增。

```
void Lock();
```

### <a name="remarks"></a>备注

出现错误时，它将引发[COleException](../../mfc/reference/coleexception-class.md)。

中的数组描述符的指针的有效截止`Unlock`调用。 调用`Lock`可以嵌套; 相同数目的调用`Unlock`所需。

锁定时，不能删除数组。

##  <a name="operator_lpcvariant"></a>  COleSafeArray::operator LPCVARIANT

调用此强制转换运算符来访问基础`VARIANT`此结构`COleSafeArray`对象。

```
operator LPCVARIANT() const;
```

##  <a name="operator_lpvariant"></a>  COleSafeArray::operator LPVARIANT

调用此强制转换运算符来访问基础`VARIANT`此结构`COleSafeArray`对象。

```
operator LPVARIANT();
```

### <a name="remarks"></a>备注

请注意，更改中的值`VARIANT`访问此函数返回的指针的结构将更改此设置的值`COleSafeArray`对象。

##  <a name="operator_eq"></a>  COleSafeArray::operator =

这些重载的赋值运算符将源值复制到此`COleSafeArray`对象。

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
  COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>备注

每个运算符的简短说明如下所示：

- **运算符 = (** *saSrc* **)** 将复制的现有`COleSafeArray`到此对象的对象。

- **运算符 = (** *varSrc* **)** 将复制的现有`VARIANT`或`COleVariant`到此对象的数组。

- **运算符 = (** *pSrc* **)** 副本`VARIANT`数组对象访问*pSrc*到此对象。

##  <a name="operator_eq_eq"></a>  COleSafeArray::operator = =

此运算符比较两个数组 (`SAFEARRAY`， `VARIANT`， `COleVariant`，或`COleSafeArray`数组)，并返回非零，如果它们是相等; 否则为 0。

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>备注

如果它们有相同数目的维度，在每个维度和相等的元素值的大小相等，则两个数组相等。

##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;

`COleSafeArray`插入 (<<) 运算符支持诊断转储和存储`COleSafeArray`对象到存档。

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex

返回指向指定的索引值的元素的指针。

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>参数

*rgIndices*<br/>
确定数组的元素的索引值的数组。 必须指定所有索引的元素。

*ppvData*<br/>
返回，指向标识中的值的元素上*rgIndices*。

##  <a name="putelement"></a>  COleSafeArray::PutElement

将单个元素分配到数组。

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>参数

*rgIndices*<br/>
指向数组的每个维度的索引数组的指针。

*pvData*<br/>
指向要分配给数组的数据的指针。 VT_DISPATCH、 VT_UNKNOWN 和 VT_BSTR 变体类型都是指针，不需要另一级间接寻址。

### <a name="remarks"></a>备注

此函数将自动调用 Windows 函数[SafeArrayLock](/windows/desktop/api/oleauto/nf-oleauto-safearraylock)并[SafeArrayUnlock](/windows/desktop/api/oleauto/nf-oleauto-safearrayunlock)之前和之后分配元素。 如果数据元素是字符串、对象或变量，则函数将正确复制它，而如果现有元素是字符串、对象或变量，则将正确清除它。

请注意，你可以在一个数组上拥有多个锁，以便在数组被其他操作锁定时可以将元素放入该数组。

出现错误时，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

##  <a name="redim"></a>  COleSafeArray::Redim

更改安全数组的最低有效 （最右边） 绑定。

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>参数

*psaboundNew*<br/>
指向新的安全数组绑定结构，它包含新数组界限。 仅最低有效位维数组可能会发生更改。

### <a name="remarks"></a>备注

出现错误时，该函数将引发[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim

一维中的元素数更改`COleSafeArray`对象。

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>参数

*dwElements*<br/>
一维的安全数组中的元素数。

### <a name="remarks"></a>备注

出现错误时，该函数将引发[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

  有关示例，请参阅[COleSafeArray::CreateOneDim](#createonedim)。

##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData

递减锁计数数组，使无效指针来检索`AccessData`。

```
void UnaccessData();
```

### <a name="remarks"></a>备注

出现错误时，该函数将引发[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

  有关示例，请参阅[COleSafeArray::AccessData](#accessdata)。

##  <a name="unlock"></a>  COleSafeArray::Unlock

减少锁计数的一个数组，因此它可以释放或调整大小。

```
void Unlock();
```

### <a name="remarks"></a>备注

完成对数组中数据的访问后，调用此函数。 出现错误时，它将引发[COleException](../../mfc/reference/coleexception-class.md)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 类](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
