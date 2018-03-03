---
title: "CComSafeArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7bed846015090ef9c4da841adff4968c91d8719d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomsafearray-class"></a>CComSafeArray 类
此类是 **SAFEARRAY** 结构的包装器。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在数组中的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComSafeArray::CComSafeArray](#ccomsafearray)|构造函数。|  
|[CComSafeArray:: ~ CComSafeArray](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComSafeArray::Add](#add)|将一个或多个元素或 **SAFEARRAY** 结构添加到 `CComSafeArray`。|  
|[CComSafeArray::Attach](#attach)|将 **SAFEARRAY** 结构附加到 `CComSafeArray` 对象。|  
|[CComSafeArray::CopyFrom](#copyfrom)|将 **SAFEARRAY** 结构的内容复制到 `CComSafeArray` 对象中。|  
|[CComSafeArray::CopyTo](#copyto)|创建 `CComSafeArray` 对象的副本。|  
|[CComSafeArray::Create](#create)|创建一个 `CComSafeArray` 对象。|  
|[CComSafeArray::Destroy](#destroy)|销毁 `CComSafeArray` 对象。|  
|[CComSafeArray::Detach](#detach)|从 **对象拆离** SAFEARRAY `CComSafeArray` 。|  
|[CComSafeArray::GetAt](#getat)|从一维数组中检索单个元素。|  
|[CComSafeArray::GetCount](#getcount)|返回数组中的元素数目。|  
|[CComSafeArray::GetDimensions](#getdimensions)|返回数组中的维数。|  
|[CComSafeArray::GetLowerBound](#getlowerbound)|返回数组给定维度的下限。|  
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|返回 `m_psa` 数据成员的地址。|  
|[CComSafeArray::GetType](#gettype)|返回数组中存储的数据类型。|  
|[CComSafeArray::GetUpperBound](#getupperbound)|返回数组任意维度的上限。|  
|[CComSafeArray::IsSizable](#issizable)|测试是否可重设 `CComSafeArray` 对象的大小。|  
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|从多维数组中检索单个元素。|  
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|设置多维数组中元素的值。|  
|[CComSafeArray::Resize](#resize)|重设 `CComSafeArray` 对象的大小。|  
|[CComSafeArray::SetAt](#setat)|设置一维数组中元素的值。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|将值转换为 **SAFEARRAY** 指针。|  
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|从数组中检索元素。|  
|[CComSafeArray::operator =](#operator_eq)|赋值运算符。|  

  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComSafeArray::m_psa](#m_psa)|此数据成员保留 **SAFEARRAY** 结构的地址。|  
  
## <a name="remarks"></a>备注  
 `CComSafeArray` 为 [SAFEARRAY Data Type](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e) 类提供包装器，从而可以轻松地创建并管理几乎所有支持 VARIANT 的类型的一维数组和多维数组。  
  
 `CComSafeArray` 可简化数组在进程之间的传递，此外还可以对照上限和下限检查数组索引值，从而提供额外的安全性。  
  
 `CComSafeArray` 的下限可以从任何用户定义值开始；但是，通过 C++ 访问的数组应该使用下限 0。 Visual Basic 等其他语言可以使用其他边界值（例如，-10 到 10）。  
  
 使用 [CComSafeArray::Create](#create) 可以创建 `CComSafeArray` 对象，使用 [CComSafeArray::Destroy](#destroy) 可将其删除。  
  
 `CComSafeArray` 可以包含以下 VARIANT 数据类型子集：  
  
|VARTYPE|描述|  
|-------------|-----------------|  
|VT_I1|char|  
|VT_I2|short|  
|VT_I4|int|  
|VT_I4|long|  
|VT_I8|longlong|  
|VT_UI1|byte|  
|VT_UI2|ushort|  
|VT_UI4|uint|  
|VT_UI4|ulong|  
|VT_UI8|ulonglong|  
|VT_R4|float|  
|VT_R8|double|  
|VT_DECIMAL|十进制指针|  
|VT_VARIANT|变体指针|  
|VT_CY|货币数据类型|  
  
## <a name="requirements"></a>惠?  
 **标头：** atlsafe.h  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]  
  
##  <a name="add"></a>CComSafeArray::Add  
 将一个或多个元素或 **SAFEARRAY** 结构添加到 `CComSafeArray`。  
  
```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `psaSrc`  
 指向的指针**SAFEARRAY**对象。  
  
 `ulCount`  
 要添加到数组的对象数。  
  
 *pT*  
 指向要添加到数组的一个或多个对象的指针。  
  
 *t*  
 对要添加到数组的对象的引用。  
  
 `bCopy`  
 指示是否应创建数据的副本。 默认值是**TRUE**。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 新对象追加到现有的末尾**SAFEARRAY**对象。 对象添加到多维**SAFEARRAY**不支持对象。 在添加现有对象的数组时，这两个数组必须包含相同类型的元素。  
  
 `bCopy`考虑标志时类型的元素`BSTR`或**VARIANT**添加到数组。 默认值**TRUE**可确保当该元素添加到数组的数据创建一个新副本。  
  
##  <a name="attach"></a>CComSafeArray::Attach  
 将 **SAFEARRAY** 结构附加到 `CComSafeArray` 对象。  
  
```
HRESULT Attach(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>参数  
 `psaSrc`  
 指向的指针**SAFEARRAY**结构。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 将附加**SAFEARRAY**结构`CComSafeArray`对象，使现有`CComSafeArray`可用的方法。  
  
##  <a name="ccomsafearray"></a>CComSafeArray::CComSafeArray  
 构造函数。  
  
```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>参数  
 `bound`  
 A **SAFEARRAYBOUND**结构。  
  
 `ulCount`  
 数组中的元素数。  
  
 `lLBound`  
 下限值，则为即，数组中的第一个元素的索引。  
  
 `pBound`  
 指向的指针**SAFEARRAYBOUND**结构。  
  
 `uDims`  
 数组中的维度的计数。  
  
 `saSrc`  
 对引用**SAFEARRAY**结构或`CComSafeArray`对象。 在任一情况下构造函数使用此引用制作该数组的副本，以便完成构造后所不引用的数组。  
  
 `psaSrc`  
 指向的指针**SAFEARRAY**结构。 构造函数使用此地址制作该数组的副本，以便完成构造后所不引用的数组。  
  
### <a name="remarks"></a>备注  
 创建一个 `CComSafeArray` 对象。  
  
##  <a name="dtor"></a>CComSafeArray:: ~ CComSafeArray  
 析构函数。  
  
```
~CComSafeArray() throw()
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="copyfrom"></a>CComSafeArray::CopyFrom  
 将 **SAFEARRAY** 结构的内容复制到 `CComSafeArray` 对象中。  
  
```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>参数  
 `ppArray`  
 指向**SAFEARRAY**复制。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 此方法将内容复制**SAFEARRAY**到当前`CComSafeArray`对象。 将替换现有数组的内容。  
  
##  <a name="copyto"></a>CComSafeArray::CopyTo  
 创建 `CComSafeArray` 对象的副本。  
  
```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>参数  
 `ppArray`  
 指向要在其中创建新的位置的指针**SAFEARRAY**。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 此方法将内容复制`CComSafeArray`对象插入**SAFEARRAY**结构。  
  
##  <a name="create"></a>  CComSafeArray::Create  
 创建一个 `CComSafeArray`。  
  
```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>参数  
 `pBound`  
 指向的指针**SAFEARRAYBOUND**对象。  
  
 `uDims`  
 数组中的维度数。  
  
 `ulCount`  
 数组中的元素数。  
  
 `lLBound`  
 下限值，则为即，数组中的第一个元素的索引。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 A`CComSafeArray`对象可以创建从现有**SAFEARRAYBOUND**结构和数目的维度，或者按指定的元素数，在使用数组和下限。 如果数组为从 Visual c + + 中访问，下限应为 0。 其他语言可能允许其他值下限 （例如，如-10 到 10 范围的元素的 Visual 基本支持阵列）。  
  
##  <a name="destroy"></a>  CComSafeArray::Destroy  
 销毁 `CComSafeArray` 对象。  
  
```
HRESULT Destroy();
```  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 销毁现有`CComSafeArray`对象及其所有包含的数据。  
  
##  <a name="detach"></a>CComSafeArray::Detach  
 从 **对象拆离** SAFEARRAY `CComSafeArray` 。  
  
```
LPSAFEARRAY Detach();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向**SAFEARRAY**对象。  
  
### <a name="remarks"></a>备注  
 此方法将分离**SAFEARRAY**对象`CComSafeArray`对象。  
  
##  <a name="getat"></a>CComSafeArray::GetAt  
 从一维数组中检索单个元素。  
  
```
T& GetAt(LONG lIndex) const;
```  
  
### <a name="parameters"></a>参数  
 `lIndex`  
 要返回的数组中的值的索引号。  
  
### <a name="return-value"></a>返回值  
 返回所需的数组元素的引用。  
  
##  <a name="getcount"></a>CComSafeArray::GetCount  
 返回数组中的元素数目。  
  
```
ULONG GetCount(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>参数  
 `uDim`  
 数组维度中。  
  
### <a name="return-value"></a>返回值  
 返回数组中的元素数目。  
  
### <a name="remarks"></a>备注  
 当与多维数组一起使用，此方法将仅由特定维度中返回元素的数。  
  
##  <a name="getdimensions"></a>CComSafeArray::GetDimensions  
 返回数组中的维数。  
  
```
UINT GetDimensions() const;
```  
  
### <a name="return-value"></a>返回值  
 返回数组中的维数。  
  
##  <a name="getlowerbound"></a>CComSafeArray::GetLowerBound  
 返回数组给定维度的下限。  
  
```
LONG GetLowerBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>参数  
 `uDim`  
 要为其获取下限数组维度。 如果省略，默认值为 0。  
  
### <a name="return-value"></a>返回值  
 返回下限。  
  
### <a name="remarks"></a>备注  
 如果下限为 0，则表明其第一个元素为元素编号为 0 的类似 C 的数组。 发生错误，例如，维度无效自变量，此方法调用`AtlThrow`与描述该错误的 HRESULT。  
  
##  <a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr  
 返回 `m_psa` 数据成员的地址。  
  
```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向[CComSafeArray::m_psa](#m_psa)数据成员。  
  
##  <a name="gettype"></a>CComSafeArray::GetType  
 返回数组中存储的数据类型。  
  
```
VARTYPE GetType() const;
```  
  
### <a name="return-value"></a>返回值  
 返回存储在数组中，这可能是任何以下类型的数据类型：  
  
|VARTYPE|描述|  
|-------------|-----------------|  
|VT_I1|char|  
|VT_I2|short|  
|VT_I4|int|  
|VT_I4|long|  
|VT_I8|longlong|  
|VT_UI1|byte|  
|VT_UI2|ushort|  
|VT_UI4|uint|  
|VT_UI4|ulong|  
|VT_UI8|ulonglong|  
|VT_R4|float|  
|VT_R8|double|  
|VT_DECIMAL|十进制指针|  
|VT_VARIANT|变体指针|  
|VT_CY|货币数据类型|  
  
##  <a name="getupperbound"></a>CComSafeArray::GetUpperBound  
 返回数组任意维度的上限。  
  
```
LONG GetUpperBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>参数  
 `uDim`  
 要为其获取上限数组维度。 如果省略，默认值为 0。  
  
### <a name="return-value"></a>返回值  
 返回的上限。 此值是 （含），此维度的最大有效索引。  
  
### <a name="remarks"></a>备注  
 发生错误，例如，维度无效自变量，此方法调用`AtlThrow`与描述该错误的 HRESULT。  
  
##  <a name="issizable"></a>CComSafeArray::IsSizable  
 测试是否可重设 `CComSafeArray` 对象的大小。  
  
```
bool IsSizable() const;
```  
  
### <a name="return-value"></a>返回值  
 返回**true**如果`CComSafeArray`可调整大小， **false**如果它不能。  
  
##  <a name="m_psa"></a>CComSafeArray::m_psa  
 保留的地址**SAFEARRAY**访问的结构。  
  
```
LPSAFEARRAY m_psa;
```  
  
##  <a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt  
 从多维数组中检索单个元素。  
  
```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```  
  
### <a name="parameters"></a>参数  
 `alIndex`  
 指向数组中每个维度的索引的向量。 最左侧 （最不重要） 的维度是`alIndex[0]`。  
  
 *t*  
 对返回的数据的引用。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="multidimsetat"></a>CComSafeArray::MultiDimSetAt  
 设置多维数组中元素的值。  
  
```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```  
  
### <a name="parameters"></a>参数  
 `alIndex`  
 指向数组中每个维度的索引的向量。 最右边的 （最不重要） 维度是`alIndex`[0]。  
  
 *T*  
 指定新的元素的值。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 这是多维版本[CComSafeArray::SetAt](#setat)。  
  
##  <a name="operator_at"></a>CComSafeArray::operator\[\]  
 从数组中检索元素。  
  
```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```  
  
### <a name="parameters"></a>参数  
 *索引 nIndex*  
 数组中所需元素的索引号。  
  
### <a name="return-value"></a>返回值  
 返回适当的数组元素。  
  
### <a name="remarks"></a>备注  
 执行到相似的功能[CComSafeArray::GetAt](#getat)，但此运算符仅适用于一维数组。  
  
##  <a name="operator_eq"></a>CComSafeArray::operator =  
 赋值运算符。  
  
```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>参数  
 `saSrc`  
 对 `CComSafeArray` 对象的引用。  
  
 `psaSrc`  
 指向的指针**SAFEARRAY**对象。  
  
### <a name="return-value"></a>返回值  
 返回数组中存储的数据类型。  
  
##  <a name="operator_lpsafearray"></a>CComSafeArray::operator LPSAFEARRAY  
 将值转换为 **SAFEARRAY** 指针。  
  
```
operator LPSAFEARRAY() const;
```  
  
### <a name="return-value"></a>返回值  
 将值转换为 **SAFEARRAY** 指针。  
  
##  <a name="resize"></a>CComSafeArray::Resize  
 重设 `CComSafeArray` 对象的大小。  
  
```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>参数  
 `pBound`  
 指向的指针**SAFEARRAYBOUND**结构，其中包含有关元素的数目和数组的下限。  
  
 `ulCount`  
 请求的调整大小的数组中的对象数。  
  
 `lLBound`  
 下限。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 此方法仅调整大小时最右边的维度。 它将不调整大小返回的数组**IsResizable**作为**false**。  
  
##  <a name="setat"></a>CComSafeArray::SetAt  
 设置一维数组中元素的值。  
  
```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lIndex`  
 要设置的数组元素的索引号。  
  
 *t*  
 指定元素的新值。  
  
 `bCopy`  
 指示是否应创建数据的副本。 默认值是**TRUE**。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 `bCopy`考虑标志时类型的元素`BSTR`或**VARIANT**添加到数组。 默认值**TRUE**可确保当该元素添加到数组的数据创建一个新副本。  
  
## <a name="see-also"></a>请参阅  
 [SAFEARRAY Data Type](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e)   
 [Ccomsafearray:: Create](#create)   
 [Ccomsafearray:: Destroy](#destroy)   
 [类概述](../../atl/atl-class-overview.md)
