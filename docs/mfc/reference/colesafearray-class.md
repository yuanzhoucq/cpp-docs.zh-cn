---
title: COleSafeArray 类
ms.date: 08/29/2019
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
ms.openlocfilehash: a7be9910b573cb5bc430d6608e75ce6661b71bc2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374867"
---
# <a name="colesafearray-class"></a>COleSafeArray 类

与任意类型和维度的数组一起使用的类。

## <a name="syntax"></a>语法

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleSafearray：COleSafearray](#colesafearray)|构造 `COleSafeArray` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleSafearray：访问数据](#accessdata)|检索指向数组数据的指针。|
|[COleSafearray：allocData](#allocdata)|为数组分配内存。|
|[COleSafearray：：均等描述符](#allocdescriptor)|为安全数组描述符分配内存。|
|[COleSafearray：附加](#attach)|将现有`VARIANT`数组的控制权授予`COleSafeArray`对象。|
|[COleSafearray：清除](#clear)|释放基础`VARIANT`中的所有数据。|
|[COleSafearray：复制](#copy)|创建现有数组的副本。|
|[COleSafearray：创建](#create)|创建安全数组。|
|[COleSafearray：创建一个Dim](#createonedim)|创建一维`COleSafeArray`对象。|
|[COleSafeArray：:D](#destroy)|销毁现有数组。|
|[COleSafeArray：:D](#destroydata)|销毁安全数组中的数据。|
|[COleSafeArray：:D描述符](#destroydescriptor)|销毁安全数组的描述符。|
|[COleSafearray：:D埃塔奇](#detach)|从`COleSafeArray`对象分离 VARIANT 数组（以便不会释放数据）。|
|[COleSafearray：获取字节数组](#getbytearray)|将安全数组的内容复制到[CByteArray](../../mfc/reference/cbytearray-class.md)中。|
|[COleSafearray：GetDim](#getdim)|返回数组中的维数。|
|[COleSafearray：获取元素](#getelement)|检索安全数组的单个元素。|
|[COleSafearray：获取Elemsize](#getelemsize)|返回安全数组中一个元素的大小（以字节为单位）。|
|[COleSafearray：GetLBound](#getlbound)|返回安全数组的任何维度的下限。|
|[COleSafearray：获取一个Dimmsize](#getonedimsize)|返回一维`COleSafeArray`对象中的元素数。|
|[COleSafearray：GetUBund](#getubound)|返回安全数组的任何维度的上限。|
|[COleSafearray：锁](#lock)|增加数组的锁计数，并在数组描述符中放置指向数组数据的指针。|
|[COleSafearray：:PtrofIndex](#ptrofindex)|返回指向索引元素的指针。|
|[COleSafearray：:Put元素](#putelement)|将单个元素分配到数组。|
|[COleSafearray：雷西姆](#redim)|更改安全数组的最小显著（最右）绑定。|
|[COleSafearray：调整一个Dim的大小](#resizeonedim)|更改一维`COleSafeArray`对象中的元素数。|
|[COleSafearray：取消访问数据](#unaccessdata)|删除数组的锁计数，使 检索到`AccessData`的指针无效。|
|[COleSafearray：解锁](#unlock)|对数组的锁计数进行缩减，以便可以释放或调整大小。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[COleSafearray：：操作员LPCVARIANT](#operator_lpcvariant)|访问`VARIANT``COleSafeArray`对象的基础结构。|
|[COleSafearray：：操作员LPVARIANT](#operator_lpvariant)|访问`VARIANT``COleSafeArray`对象的基础结构。|
|[COleSafeArray：：操作员 |](#operator_eq)|`COleSafeArray`将值复制到对象 （、、`COleVariant``COleSafeArray``SAFEARRAY``VARIANT`或数组）。|
|[COleSafeArray：：操作员 |](#operator_eq_eq)|比较两`SAFEARRAY`个变体数组（、、、`VARIANT``COleVariant`或`COleSafeArray`数组）。|
|[COleSafeArray：：操作员&lt;&lt;](#operator_lt_lt)|将`COleSafeArray`对象的内容输出到转储上下文。|

## <a name="remarks"></a>备注

`COleSafeArray`派生自 OLE`VARIANT`结构。 OLE`SAFEARRAY`成员函数可通过 以及`COleSafeArray`专为字节的一维数组设计的一组成员函数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="colesafearrayaccessdata"></a><a name="accessdata"></a>COleSafearray：访问数据

检索指向数组数据的指针。

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>参数

*ppvData*<br/>
指向数组数据的指针。

### <a name="remarks"></a>备注

错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

## <a name="colesafearrayallocdata"></a><a name="allocdata"></a>COleSafearray：allocData

为安全数组分配内存。

```
void AllocData();
```

### <a name="remarks"></a>备注

错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a>COleSafearray：：均等描述符

为安全数组的描述符分配内存。

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>参数

*德迪姆斯*<br/>
安全数组中的维度数。

### <a name="remarks"></a>备注

错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearrayattach"></a><a name="attach"></a>COleSafearray：附加

将现有`VARIANT`数组中的数据控制权授予`COleSafeArray`对象。

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>参数

*varSrc*<br/>
`VARIANT` 对象。 *varSrc*参数必须具有 VARTYPE [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)。

### <a name="remarks"></a>备注

源`VARIANT`的类型设置为VT_EMPTY。 此函数清除当前数组数据（如果有）。

### <a name="example"></a>示例

  请参阅[COleSafeArray 的示例：访问数据](#accessdata)。

## <a name="colesafearrayclear"></a><a name="clear"></a>COleSafearray：清除

清除安全数组。

```
void Clear();
```

### <a name="remarks"></a>备注

该函数通过将对象`VARTYPE`设置为VT_EMPTY来清除安全数组。 释放当前内容并释放数组。

## <a name="colesafearraycolesafearray"></a><a name="colesafearray"></a>COleSafearray：COleSafearray

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

*萨斯尔克*<br/>
现有`COleSafeArray`对象或`SAFEARRAY`要复制到新`COleSafeArray`对象。

*弗茨尔克*<br/>
新`COleSafeArray`对象的 VARTYPE。

*普萨斯克*<br/>
`SAFEARRAY`要复制到新`COleSafeArray`对象的 指针。

*varSrc*<br/>
要复制到`VARIANT`新`COleVariant``COleSafeArray`对象的现有或对象。

*pSrc*<br/>
指向要复制到新`VARIANT``COleSafeArray`对象的对象的指针。

### <a name="remarks"></a>备注

所有这些构造函数都创建新`COleSafeArray`的对象。 如果没有参数，则创建空`COleSafeArray`对象（VT_EMPTY）。 如果从其中一个数组复制的 VARTYPE 隐式已知`COleSafeArray` `COleVariant`（a `VARIANT`， 或 ）， 则保留源数组的 VARTYPE，无需指定。 `COleSafeArray` `COleSafeArray`如果从不知道 VARTYPE 的另一个数组 （），`SAFEARRAY`必须在*vtSrc*参数中指定 VARTYPE。

错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearraycopy"></a><a name="copy"></a>COleSafearray：复制

创建现有安全数组的副本。

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>参数

*普萨*<br/>
指向要返回新数组描述符的位置的指针。

### <a name="remarks"></a>备注

错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearraycreate"></a><a name="create"></a>COleSafearray：创建

分配和初始化数组的数据。

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

*弗茨尔克*<br/>
数组的基础类型（即数组每个元素的 VARTYPE）。 VARTYPE 仅限于变体类型的子集。 无法设置VT_ARRAY和VT_BYREF标志。 VT_EMPTY和VT_NULL不是数组的有效基类型。 所有其他类型都是合法的。

*德迪姆斯*<br/>
数组中的维度数。 在使用[Redim](#redim)创建数组后，可以更改此更改。

*rg元素*<br/>
指向数组中每个维度的元素数的数组。

*格萨邦*<br/>
指向边界矢量（每个维度一个）的指针，用于为数组分配。

### <a name="remarks"></a>备注

如有必要，此函数将清除当前数组数据。 错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraycreateonedim"></a><a name="createonedim"></a>COleSafearray：创建一个Dim

创建新的一维`COleSafeArray`对象。

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>参数

*弗茨尔克*<br/>
数组的基础类型（即数组每个元素的 VARTYPE）。

*dwElements*<br/>
数组中的元素数。 在使用[ResizeOneDim](#resizeonedim)创建数组后，可以更改此更改。

*pvSrcData*<br/>
指向要复制到数组的数据的指针。

*nLBound*<br/>
数组的下限。

### <a name="remarks"></a>备注

函数分配和初始化数组的数据，如果指针*pvSrcData*不是 NULL，则复制指定的数据。

错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

## <a name="colesafearraydestroy"></a><a name="destroy"></a>COleSafeArray：:D

销毁现有数组描述符和数组中的所有数据。

```
void Destroy();
```

### <a name="remarks"></a>备注

如果对象存储在数组中，则释放每个对象。 错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearraydestroydata"></a><a name="destroydata"></a>COleSafeArray：:D

销毁安全数组中的所有数据。

```
void DestroyData();
```

### <a name="remarks"></a>备注

如果对象存储在数组中，则释放每个对象。 错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a>COleSafeArray：:D描述符

销毁安全数组的描述符。

```
void DestroyDescriptor();
```

### <a name="remarks"></a>备注

错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearraydetach"></a><a name="detach"></a>COleSafearray：:D埃塔奇

从`COleSafeArray`对象分离`VARIANT`数据。

```
VARIANT Detach();
```

### <a name="return-value"></a>返回值

对象中`VARIANT``COleSafeArray`的基础值。

### <a name="remarks"></a>备注

该函数通过将对象的 VARTYPE 设置为VT_EMPTY来分离安全数组中的数据。 调用方有责任通过调用 Windows 函数[VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)来释放数组。

错误时，函数将抛出一个[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

  请参阅[COleSafeArray：:PutElement](#putelement)） 的示例。

## <a name="colesafearraygetbytearray"></a><a name="getbytearray"></a>COleSafearray：获取字节数组

将安全数组的内容复制到 中`CByteArray`。

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>参数

*字节*<br/>
对[CByteArray](../../mfc/reference/cbytearray-class.md)对象的引用。

## <a name="colesafearraygetdim"></a><a name="getdim"></a>COleSafearray：GetDim

返回对象中的`COleSafeArray`维度数。

```
DWORD GetDim();
```

### <a name="return-value"></a>返回值

安全数组中的维度数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraygetelement"></a><a name="getelement"></a>COleSafearray：获取元素

检索安全数组的单个元素。

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>参数

*rg索引*<br/>
指向数组的每个维度的索引数组的指针。

*pvData*<br/>
指向位置以放置数组的元素。

### <a name="remarks"></a>备注

此函数自动调用窗口函数`SafeArrayLock`以及`SafeArrayUnlock`检索元素之前和之后。 如果数据元素是字符串、对象或变体，则函数以正确的方式复制该元素。 参数*pvData*应指向足够大的缓冲区以包含该元素。

错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

## <a name="colesafearraygetelemsize"></a><a name="getelemsize"></a>COleSafearray：获取Elemsize

检索`COleSafeArray`对象中元素的大小。

```
DWORD GetElemSize();
```

### <a name="return-value"></a>返回值

安全数组元素的大小（以字节为单位）。

## <a name="colesafearraygetlbound"></a><a name="getlbound"></a>COleSafearray：GetLBound

返回`COleSafeArray`对象任何维度的下限。

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>参数

*dwDim*<br/>
要为其获取下限的数组维度。

*pL绑定*<br/>
指向位置以返回下限。

### <a name="remarks"></a>备注

错误时，函数将抛出一个[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

## <a name="colesafearraygetonedimsize"></a><a name="getonedimsize"></a>COleSafearray：获取一个Dimmsize

返回一维`COleSafeArray`对象中的元素数。

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>返回值

一维安全数组中的元素数。

### <a name="example"></a>示例

  请参阅[COleSafearray 的示例：：创建OneDim](#createonedim)。

## <a name="colesafearraygetubound"></a><a name="getubound"></a>COleSafearray：GetUBund

返回安全数组的任何维度的上限。

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>参数

*dwDim*<br/>
要为其获取上限的数组维度。

*pUBound*<br/>
指向位置以返回上边界。

### <a name="remarks"></a>备注

错误时，函数将抛出一个[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

## <a name="colesafearraylock"></a><a name="lock"></a>COleSafearray：锁

增加数组的锁计数，并在数组描述符中放置指向数组数据的指针。

```
void Lock();
```

### <a name="remarks"></a>备注

错误时，它抛出一个[COleException](../../mfc/reference/coleexception-class.md)。

数组描述符中的指针在调用之前`Unlock`有效。 可以嵌套`Lock`对的调用;需要同等数量的调用`Unlock`。

数组在锁定时无法删除。

## <a name="colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleSafearray：：操作员LPCVARIANT

调用此强制转换运算符以访问此`VARIANT``COleSafeArray`对象的基础结构。

```
operator LPCVARIANT() const;
```

## <a name="colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleSafearray：：操作员LPVARIANT

调用此强制转换运算符以访问此`VARIANT``COleSafeArray`对象的基础结构。

```
operator LPVARIANT();
```

### <a name="remarks"></a>备注

请注意，更改此函数返回的`VARIANT`指针访问的结构中的值将更改此`COleSafeArray`对象的值。

## <a name="colesafearrayoperator-"></a><a name="operator_eq"></a>COleSafeArray：：操作员 |

这些重载赋值运算符将源值复制到此`COleSafeArray`对象中。

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>备注

每个运算符的简要描述如下：

- **运算符 =（** *saSrc* **）** 将现有`COleSafeArray`对象复制到此对象中。

- 运算符 **（varSrc* **operator =(** **）** 将现有`VARIANT`或`COleVariant`数组复制到此对象中。

- 运算符 *=（pSrc* **operator =(** **）** 将`VARIANT` *pSrc*访问的数组对象复制到此对象中。

## <a name="colesafearrayoperator-"></a><a name="operator_eq_eq"></a>COleSafeArray：：操作员 |

此运算符`SAFEARRAY`比较两个数组（、、、`VARIANT``COleVariant`或`COleSafeArray`数组），如果数组相等，则返回非零数组;否则 0。

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>备注

如果两个数组的维度数相等、每个维度的大小相等且元素值相等，则两个数组相等。

## <a name="colesafearrayoperator-ltlt"></a><a name="operator_lt_lt"></a>COleSafeArray：：操作员&lt;&lt;

插入`COleSafeArray`（<<）运算符支持诊断转储并将`COleSafeArray`对象存储到存档。

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

## <a name="colesafearrayptrofindex"></a><a name="ptrofindex"></a>COleSafearray：:PtrofIndex

返回指向索引值指定的元素的指针。

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>参数

*rg索引*<br/>
标识数组元素的索引值数组。 必须指定元素的所有索引。

*ppvData*<br/>
返回时，指针指向*rgIndices*中的值标识的元素。

## <a name="colesafearrayputelement"></a><a name="putelement"></a>COleSafearray：:Put元素

将单个元素分配到数组。

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>参数

*rg索引*<br/>
指向数组的每个维度的索引数组的指针。

*pvData*<br/>
指向要分配给数组的数据的指针。 VT_DISPATCH、VT_UNKNOWN和VT_BSTR变体类型是指针，不需要另一级别的间接。

### <a name="remarks"></a>备注

此函数在分配元素之前和之后自动调用 Windows 函数[SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock)和安全[ArrayUnlock。](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) 如果数据元素是字符串、对象或变量，则函数将正确复制它，而如果现有元素是字符串、对象或变量，则将正确清除它。

请注意，你可以在一个数组上拥有多个锁，以便在数组被其他操作锁定时可以将元素放入该数组。

错误时，函数将抛出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

## <a name="colesafearrayredim"></a><a name="redim"></a>COleSafearray：雷西姆

更改安全数组的最小显著（最右）绑定。

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>参数

*psabund New*<br/>
指向包含新数组绑定的新安全数组绑定结构的指针。 只能更改数组的最小尺寸。

### <a name="remarks"></a>备注

错误时，函数将抛出一个[COleException](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearrayresizeonedim"></a><a name="resizeonedim"></a>COleSafearray：调整一个Dim的大小

更改一维`COleSafeArray`对象中的元素数。

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>参数

*dwElements*<br/>
一维安全数组中的元素数。

### <a name="remarks"></a>备注

错误时，函数将抛出一个[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

  请参阅[COleSafearray 的示例：：创建OneDim](#createonedim)。

## <a name="colesafearrayunaccessdata"></a><a name="unaccessdata"></a>COleSafearray：取消访问数据

删除数组的锁计数，使 检索到`AccessData`的指针无效。

```
void UnaccessData();
```

### <a name="remarks"></a>备注

错误时，函数将抛出一个[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>示例

  请参阅[COleSafeArray 的示例：访问数据](#accessdata)。

## <a name="colesafearrayunlock"></a><a name="unlock"></a>COleSafearray：解锁

对数组的锁计数进行缩减，以便可以释放或调整大小。

```
void Unlock();
```

### <a name="remarks"></a>备注

完成对数组中数据的访问后，将调用此函数。 错误时，它抛出一个[COleException](../../mfc/reference/coleexception-class.md)。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 类](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase 类](../../mfc/reference/cdatabase-class.md)<br/>
