---
title: COleSafeArray 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b85c64837f9bc7a0c8c1873f434855d77c01fb1b
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041628"
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
|[COleSafeArray::Attach](#attach)|向提供对现有控制**VARIANT**数组到`COleSafeArray`对象。|  
|[COleSafeArray::Clear](#clear)|释放基础中的所有数据**VARIANT**。|  
|[COleSafeArray::Copy](#copy)|创建现有数组的副本。|  
|[COleSafeArray::Create](#create)|创建一个安全的数组。|  
|[COleSafeArray::CreateOneDim](#createonedim)|创建一维`COleSafeArray`对象。|  
|[COleSafeArray::Destroy](#destroy)|销毁现有数组。|  
|[COleSafeArray::DestroyData](#destroydata)|销毁安全数组中的数据。|  
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|销毁安全数组的描述符。|  
|[COleSafeArray::Detach](#detach)|分离**VARIANT**数组`COleSafeArray`对象 （以便不会释放数据）。|  
|[COleSafeArray::GetByteArray](#getbytearray)|将复制到的安全数组的内容[CByteArray](../../mfc/reference/cbytearray-class.md)。|  
|[COleSafeArray::GetDim](#getdim)|返回数组中的维数。|  
|[Colesafearray:: Getelement](#getelement)|检索安全数组的单一元素。|  
|[COleSafeArray::GetElemSize](#getelemsize)|返回的大小，以字节为单位安全数组中的一个元素。|  
|[COleSafeArray::GetLBound](#getlbound)|返回任何维度安全数组的下限。|  
|[COleSafeArray::GetOneDimSize](#getonedimsize)|返回的元素数中的一维`COleSafeArray`对象。|  
|[COleSafeArray::GetUBound](#getubound)|返回安全数组的任何维度的上限。|  
|[COleSafeArray::Lock](#lock)|数组的锁计数递增 1 并将指向数组数据的指针放在数组描述符。|  
|[COleSafeArray::PtrOfIndex](#ptrofindex)|返回指向已索引的元素的指针。|  
|[COleSafeArray::PutElement](#putelement)|将单个元素分配到数组。|  
|[COleSafeArray::Redim](#redim)|更改安全数组的最低有效 （最右边） 绑定。|  
|[COleSafeArray::ResizeOneDim](#resizeonedim)|一维中的元素数更改`COleSafeArray`对象。|  
|[COleSafeArray::UnaccessData](#unaccessdata)|递减锁计数的数组，并使无效指针检索`AccessData`。|  
|[COleSafeArray::Unlock](#unlock)|减少锁计数的一个数组以便它可以释放或调整大小。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|访问基础**VARIANT**结构`COleSafeArray`对象。|  
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|访问基础**VARIANT**结构`COleSafeArray`对象。|  
|[COleSafeArray::operator =](#operator_eq)|将复制到的值`COleSafeArray`对象 ( **SAFEARRAY**， **VARIANT**， `COleVariant`，或`COleSafeArray`数组)。|  
|[COleSafeArray::operator = =](#operator_eq_eq)|比较两个变体的数组 ( **SAFEARRAY**，**变体**， `COleVariant`，或`COleSafeArray`数组)。|  
|[COleSafeArray::operator &lt;&lt;](#operator_lt_lt)|输出的内容`COleSafeArray`到转储上下文的对象。|  
  
## <a name="remarks"></a>备注  
 `COleSafeArray` 派生自 OLE **VARIANT**结构。 OLE **SAFEARRAY**成员函数是可通过`COleSafeArray`以及作为一套专为字节的一维数组的成员函数。  
  
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
 *ppvData*  
 指向数组数据的指针的指针。  
  
### <a name="remarks"></a>备注  
 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]  
  
##  <a name="allocdata"></a>  COleSafeArray::AllocData  
 为安全数组分配内存。  
  
```  
void AllocData();
```  
  
### <a name="remarks"></a>备注  
 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="allocdescriptor"></a>  COleSafeArray::AllocDescriptor  
 为安全数组的描述符分配内存。  
  
```  
void AllocDescriptor(DWORD dwDims);
```  
  
### <a name="parameters"></a>参数  
 *dwDims*  
 在安全数组的维度数。  
  
### <a name="remarks"></a>备注  
 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="attach"></a>  COleSafeArray::Attach  
 提供对中的现有数据的控制**VARIANT**数组到`COleSafeArray`对象。  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>参数  
 *varSrc*  
 A **VARIANT**对象。 *VarSrc*参数必须具有[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)**VT_ARRAY**。  
  
### <a name="remarks"></a>备注  
 源**VARIANT**的类型设置为`VT_EMPTY`。 如果有的话，此函数将清除当前的数组数据。  
  
### <a name="example"></a>示例  
  请参阅示例[COleSafeArray::AccessData](#accessdata)。  
  
##  <a name="clear"></a>  COleSafeArray::Clear  
 清除安全数组。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 函数通过设置清除安全数组`VARTYPE`对象与`VT_EMPTY`。 发布的当前内容和数组将被释放。  
  
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
 *saSrc*  
 现有`COleSafeArray`对象或**SAFEARRAY**要复制到新`COleSafeArray`对象。  
  
 *vtSrc*  
 **VARTYPE**新`COleSafeArray`对象。  
  
 *psaSrc*  
 指向的指针**SAFEARRAY**要复制到新`COleSafeArray`对象。  
  
 *varSrc*  
 现有**VARIANT**或`COleVariant`要复制到新对象`COleSafeArray`对象。  
  
 *pSrc*  
 指向的指针**VARIANT**要复制到新对象`COleSafeArray`对象。  
  
### <a name="remarks"></a>备注  
 所有这些构造函数创建新`COleSafeArray`对象。 如果没有参数，一个空`COleSafeArray`创建对象 ( `VT_EMPTY`)。 如果`COleSafeArray`复制从另一个数组其[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)隐式已知 ( `COleSafeArray`， `COleVariant`，或**VARIANT**)，则**VARTYPE**的源数组保留，而且无需指定。 如果`COleSafeArray`复制从另一个数组其**VARTYPE**未知 ( **SAFEARRAY**)，则**VARTYPE**中必须指定*vtSrc*参数。  
  
 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="copy"></a>  COleSafeArray::Copy  
 创建现有安全数组的副本。  
  
```  
void Copy(LPSAFEARRAY* ppsa);
```  
  
### <a name="parameters"></a>参数  
 *ppsa*  
 指向要返回的新数组描述符中的位置的指针。  
  
### <a name="remarks"></a>备注  
 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
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
 *vtSrc*  
 数组的基类型 (即， **VARTYPE**的数组的每个元素)。 **VARTYPE**被限制为 variant 类型的子集。 既不**VT_ARRAY**也不**VT_BYREF**可以设置标志。 **VT_EMPTY**和**VT_NULL**就不是数组的有效基类型。 所有其他类型是合法的。  
  
 *dwDims*  
 数组中的维度数。 与创建数组后，可以更改此[Redim](#redim)。  
  
 *rgElements*  
 指向数组中每个维度的元素数的数组的指针。  
  
 *rgsabounds*  
 向量的边界 （一个用于每个维度） 的指针为数组分配。  
  
### <a name="remarks"></a>备注  
 如有必要，则此函数将清除当前的数组数据。 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)。  
  
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
 *vtSrc*  
 数组的基类型 (即， **VARTYPE**的数组的每个元素)。  
  
 *dwElements*  
 数组中的元素数目。 与创建数组后，可以更改此[ResizeOneDim](#resizeonedim)。  
  
 *pvSrcData*  
 指向要复制到数组的数据的指针。  
  
 *nLBound*  
 数组的下限。  
  
### <a name="remarks"></a>备注  
 该函数分配和初始化的数组，如果复制指定的数据的数据指针*pvSrcData*不**NULL**。  
  
 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]  
  
##  <a name="destroy"></a>  COleSafeArray::Destroy  
 销毁现有数组描述符和数组中的所有数据。  
  
```  
void Destroy();
```  
  
### <a name="remarks"></a>备注  
 如果对象存储在数组中，将释放每个对象。 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="destroydata"></a>  COleSafeArray::DestroyData  
 销毁安全数组中的所有数据。  
  
```  
void DestroyData();
```  
  
### <a name="remarks"></a>备注  
 如果对象存储在数组中，将释放每个对象。 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="destroydescriptor"></a>  COleSafeArray::DestroyDescriptor  
 销毁安全数组的描述符。  
  
```  
void DestroyDescriptor();
```  
  
### <a name="remarks"></a>备注  
 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="detach"></a>  COleSafeArray::Detach  
 分离**VARIANT**数据从`COleSafeArray`对象。  
  
```  
VARIANT Detach();
```  
  
### <a name="return-value"></a>返回值  
 基础**VARIANT**中的值`COleSafeArray`对象。  
  
### <a name="remarks"></a>备注  
 该函数将安全数组中的数据分离通过设置[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)对象与`VT_EMPTY`。 在调用方负责通过调用 Windows 函数中释放数组[VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835)。  
  
 该函数将引发错误时， [COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>示例  
  请参阅示例[COleSafeArray::PutElement](#putelement)。  
  
##  <a name="getbytearray"></a>  COleSafeArray::GetByteArray  
 将复制到的安全数组的内容`CByteArray`。  
  
```  
void GetByteArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>参数  
 *字节*  
 对引用[CByteArray](../../mfc/reference/cbytearray-class.md)对象。  
  
##  <a name="getdim"></a>  COleSafeArray::GetDim  
 返回集中的维度数目`COleSafeArray`对象。  
  
```  
DWORD GetDim();
```  
  
### <a name="return-value"></a>返回值  
 在安全数组的维度数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="getelement"></a>  Colesafearray:: Getelement  
 检索安全数组的单一元素。  
  
```  
void GetElement(
    long* rgIndices,  
    void* pvData);
```  
  
### <a name="parameters"></a>参数  
 *rgIndices*  
 指向数组的每个维度的索引数组的指针。  
  
 *pvData*  
 指向用于放置数组的元素的位置的指针。  
  
### <a name="remarks"></a>备注  
 此函数将自动调用 windows 函数`SafeArrayLock`和`SafeArrayUnlock`之前和之后在检索的元素。 如果数据元素是字符串、 对象或变体，该函数将复制正确的方式的元素。 参数*pvData*应指向大型足够的缓冲区以包含元素。  
  
 该函数将引发错误时， [CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]  
  
##  <a name="getelemsize"></a>  COleSafeArray::GetElemSize  
 检索中的某个元素的大小`COleSafeArray`对象。  
  
```  
DWORD GetElemSize();
```  
  
### <a name="return-value"></a>返回值  
 以字节为单位，安全数组的元素的大小。  
  
##  <a name="getlbound"></a>  COleSafeArray::GetLBound  
 返回任何维度的下限`COleSafeArray`对象。  
  
```  
void GetLBound(
    DWORD dwDim,  
    long* pLBound);
```  
  
### <a name="parameters"></a>参数  
 *dwDim*  
 要为其获取下限数组维度。  
  
 *pLBound*  
 指向要返回下限的位置的指针。  
  
### <a name="remarks"></a>备注  
 该函数将引发错误时， [COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]  
  
##  <a name="getonedimsize"></a>  COleSafeArray::GetOneDimSize  
 返回的元素数中的一维`COleSafeArray`对象。  
  
```  
DWORD GetOneDimSize();
```  
  
### <a name="return-value"></a>返回值  
 中的一维的安全数组的元素数。  
  
### <a name="example"></a>示例  
  请参阅示例[COleSafeArray::CreateOneDim](#createonedim)。  
  
##  <a name="getubound"></a>  COleSafeArray::GetUBound  
 返回安全数组的任何维度的上限。  
  
```  
void GetUBound(
    DWORD dwDim,  
    long* pUBound);
```  
  
### <a name="parameters"></a>参数  
 *dwDim*  
 要为其获取上限数组维度。  
  
 *pUBound*  
 指向要返回上限的位置的指针。  
  
### <a name="remarks"></a>备注  
 该函数将引发错误时， [COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]  
  
##  <a name="lock"></a>  COleSafeArray::Lock  
 数组中，然后位置指向数组数据数组描述符中的锁计数递增 1。  
  
```  
void Lock();
```  
  
### <a name="remarks"></a>备注  
 错误时，它将引发[COleException](../../mfc/reference/coleexception-class.md)。  
  
 指针数组描述符中的有效截止`Unlock`调用。 调用`Lock`可以嵌套; 对的调用的数量相等`Unlock`所需。  
  
 锁定时，无法删除数组。  
  
##  <a name="operator_lpcvariant"></a>  COleSafeArray::operator LPCVARIANT  
 调用此强制转换运算符来访问基础**VARIANT**此结构`COleSafeArray`对象。  
  
```  
operator LPCVARIANT() const;  
```  
  
##  <a name="operator_lpvariant"></a>  COleSafeArray::operator LPVARIANT  
 调用此强制转换运算符来访问基础**VARIANT**此结构`COleSafeArray`对象。  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>备注  
 请注意该更改中的值**VARIANT**访问通过此函数返回的指针的结构将更改此值`COleSafeArray`对象。  
  
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
  
- **运算符 = (** *varSrc * * *)** 将复制的现有**VARIANT**或`COleVariant`到此对象数组。  
  
- **运算符 = (** `pSrc` **)** 副本**VARIANT**数组对象访问`pSrc`到此对象。  
  
##  <a name="operator_eq_eq"></a>  COleSafeArray::operator = =  
 此运算符比较两个数组 ( **SAFEARRAY**， **VARIANT**， `COleVariant`，或`COleSafeArray`数组)，并返回非零，它们是否相等; 否则为 0。  
  
```  
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;  
   
BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;  
   
BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;  ```  
  
### Remarks  
 Two arrays are equal if they have an equal number of dimensions, equal size in each dimension, and equal element values.  
  
##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;  
 The `COleSafeArray` insertion (<<) operator supports diagnostic dumping and storing of a `COleSafeArray` object to an archive.  
  
```  
CDumpContext & AFXAPI 运算符 << (CDumpContext & dc，  
    COleSafeArray & saSrc);
```  
  
##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex  
 Returns a pointer to the element specified by the index values.  
  
```  
void PtrOfIndex (long 类型的值 * rgIndices，  
    void * * ppvData);
```  
  
### Parameters  
 *rgIndices*  
 An array of index values that identify an element of the array. All indexes for the element must be specified.  
  
 *ppvData*  
 On return, pointer to the element identified by the values in *rgIndices*.  
  
##  <a name="putelement"></a>  COleSafeArray::PutElement  
 Assigns a single element into the array.  
  
```  
void PutElement (long 类型的值 * rgIndices，  
    void * pvData);
```  
  
### Parameters  
 *rgIndices*  
 Pointer to an array of indexes for each dimension of the array.  
  
 *pvData*  
 Pointer to the data to assign to the array. **VT_DISPATCH**, **VT_UNKNOWN**, and **VT_BSTR** variant types are pointers and do not require another level of indirection.  
  
### Remarks  
 This function automatically calls the Windows functions [SafeArrayLock](https://msdn.microsoft.com/library/windows/desktop/ms221492.aspx) and [SafeArrayUnlock](https://msdn.microsoft.com/library/windows/desktop/ms221246.aspx) before and after assigning the element. If the data element is a string, object, or variant, the function copies it correctly, and if the existing element is a string, object, or variant, it is cleared correctly.  
  
 Note that you can have multiple locks on an array, so you can put elements into an array while the array is locked by other operations.  
  
 On error, the function throws a [CMemoryException](../../mfc/reference/cmemoryexception-class.md) or [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
 [!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]  
  
##  <a name="redim"></a>  COleSafeArray::Redim  
 Changes the least significant (rightmost) bound of a safe array.  
  
```  
void Redim (SAFEARRAYBOUND * psaboundNew);
```  
  
### Parameters  
 *psaboundNew*  
 Pointer to a new safe array bound structure containing the new array bound. Only the least significant dimension of an array may be changed.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim  
 Changes the number of elements in a one-dimensional `COleSafeArray` object.  
  
```  
void ResizeOneDim (DWORD dwElements);
```  
  
### Parameters  
 *dwElements*  
 Number of elements in the one-dimensional safe array.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::CreateOneDim](#createonedim).  
  
##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData  
 Decrements the lock count of an array and invalidates the pointer retrieved by `AccessData`.  
  
```  
void UnaccessData();
```  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::AccessData](#accessdata).  
  
##  <a name="unlock"></a>  COleSafeArray::Unlock  
 Decrements the lock count of an array so it can be freed or resized.  
  
```  
void Unlock();
```  
  
### Remarks  
 This function is called after access to the data in an array is finished. On error, it throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
## See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)
