---
title: "CComSafeArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeArray
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e78c0cb7a0e2fb6cc1e1ac4bba9186d4beee98b4
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CComSafeArray::CComSafeArray](#ccomsafearray)|构造函数。|  
|[CComSafeArray:: ~ CComSafeArray](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
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
  
|名称|说明|  
|----------|-----------------|  
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|将值转换为 **SAFEARRAY** 指针。|  
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|从数组中检索元素。|  
|[CComSafeArray::operator =](#operator_eq)|赋值运算符。|  

  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CComSafeArray::m_psa](#m_psa)|此数据成员保留 **SAFEARRAY** 结构的地址。|  
  
## <a name="remarks"></a>备注  
 `CComSafeArray`提供的包装[SAFEARRAY 数据类型](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e)类，使其非常简单的事情，可以创建和管理的几乎任何变体支持的类型的单个会话和多维数组。  
  
 `CComSafeArray` 可简化数组在进程之间的传递，此外还可以对照上限和下限检查数组索引值，从而提供额外的安全性。  
  
 `CComSafeArray` 的下限可以从任何用户定义值开始；但是，通过 C++ 访问的数组应该使用下限 0。 Visual Basic 等其他语言可以使用其他边界值（例如，-10 到 10）。  
  
 使用[CComSafeArray::Create](#create)创建`CComSafeArray`对象，并[CComSafeArray::Destroy](#destroy)可将其删除。  
  
 `CComSafeArray` 可以包含以下 VARIANT 数据类型子集：  
  
|VARTYPE|说明|  
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
  
## <a name="requirements"></a>要求  
 **标头：** atlsafe.h  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&75;](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]  
  
##  <a name="a-nameadda--ccomsafearrayadd"></a><a name="add"></a>CComSafeArray::Add  
 将一个或多个元素或 **SAFEARRAY** 结构添加到 `CComSafeArray`。  
  
```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `psaSrc`  
 一个指向**SAFEARRAY**对象。  
  
 `ulCount`  
 要添加到数组的对象数量。  
  
 *pT*  
 指向要添加到数组的一个或多个对象的指针。  
  
 *t*  
 对要添加到数组的对象的引用。  
  
 `bCopy`  
 指示是否应创建数据的副本。 默认值是**TRUE**。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 新对象追加到现有的末尾**SAFEARRAY**对象。 将对象添加到多维**SAFEARRAY**不支持对象。 添加现有对象的数组，当两个数组必须包含相同类型的元素。  
  
 `bCopy`标志考虑在内时类型的元素`BSTR`或**VARIANT**添加到数组。 默认值为**TRUE**可确保在该元素已添加到数组时的数据创建一个新副本。  
  
##  <a name="a-nameattacha--ccomsafearrayattach"></a><a name="attach"></a>CComSafeArray::Attach  
 将 **SAFEARRAY** 结构附加到 `CComSafeArray` 对象。  
  
```
HRESULT Attach(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>参数  
 `psaSrc`  
 一个指向**SAFEARRAY**结构。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 将附加**SAFEARRAY**结构`CComSafeArray`对象，这使得现有`CComSafeArray`可用方法。  
  
##  <a name="a-nameccomsafearraya--ccomsafearrayccomsafearray"></a><a name="ccomsafearray"></a>CComSafeArray::CComSafeArray  
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
 一个**SAFEARRAYBOUND**结构。  
  
 `ulCount`  
 数组中的元素数。  
  
 `lLBound`  
 下限值，则为即，数组中的第一个元素的索引。  
  
 `pBound`  
 一个指向**SAFEARRAYBOUND**结构。  
  
 `uDims`  
 数组中的维度数。  
  
 `saSrc`  
 对引用**SAFEARRAY**结构或`CComSafeArray`对象。 在任一情况下构造函数使用此引用来制作该数组的副本，以便完成构造后所未引用的数组。  
  
 `psaSrc`  
 一个指向**SAFEARRAY**结构。 构造函数使用此地址来制作该数组的副本，以便完成构造后所未引用的数组。  
  
### <a name="remarks"></a>备注  
 创建一个 `CComSafeArray` 对象。  
  
##  <a name="a-namedtora--ccomsafearrayccomsafearray"></a><a name="dtor"></a>CComSafeArray:: ~ CComSafeArray  
 析构函数。  
  
```
~CComSafeArray() throw()
```  
  
### <a name="remarks"></a>备注  
 释放所有已分配的资源。  
  
##  <a name="a-namecopyfroma--ccomsafearraycopyfrom"></a><a name="copyfrom"></a>CComSafeArray::CopyFrom  
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
 此方法将复制的内容**SAFEARRAY**到当前`CComSafeArray`对象。 将替换该数组的现有内容。  
  
##  <a name="a-namecopytoa--ccomsafearraycopyto"></a><a name="copyto"></a>CComSafeArray::CopyTo  
 创建 `CComSafeArray` 对象的副本。  
  
```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>参数  
 `ppArray`  
 指向要在其中创建新位置的指针**SAFEARRAY**。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 此方法将复制的内容`CComSafeArray`对象插入**SAFEARRAY**结构。  
  
##  <a name="a-namecreatea--ccomsafearraycreate"></a><a name="create"></a>CComSafeArray::Create  
 创建一个 `CComSafeArray`。  
  
```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>参数  
 `pBound`  
 一个指向**SAFEARRAYBOUND**对象。  
  
 `uDims`  
 数组中的维度数。  
  
 `ulCount`  
 数组中的元素数。  
  
 `lLBound`  
 下限值，则为即，数组中的第一个元素的索引。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 一个`CComSafeArray`对象可以创建从现有**SAFEARRAYBOUND**结构和数字的维度，或通过在该数组和下限中指定的元素数。 如果数组是从 Visual c + + 进行访问，下限应为 0。 其他语言可能允许其他值下限 （例如，Visual Basic 支持数组元素，如-10 到 10 期）。  
  
##  <a name="a-namedestroya--ccomsafearraydestroy"></a><a name="destroy"></a>CComSafeArray::Destroy  
 销毁 `CComSafeArray` 对象。  
  
```
HRESULT Destroy();
```  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 销毁现有`CComSafeArray`对象及其所有其包含的数据。  
  
##  <a name="a-namedetacha--ccomsafearraydetach"></a><a name="detach"></a>CComSafeArray::Detach  
 从 **对象拆离** SAFEARRAY `CComSafeArray` 。  
  
```
LPSAFEARRAY Detach();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向**SAFEARRAY**对象。  
  
### <a name="remarks"></a>备注  
 此方法将分离**SAFEARRAY**对象从`CComSafeArray`对象。  
  
##  <a name="a-namegetata--ccomsafearraygetat"></a><a name="getat"></a>CComSafeArray::GetAt  
 从一维数组中检索单个元素。  
  
```
T& GetAt(LONG lIndex) const;
```  
  
### <a name="parameters"></a>参数  
 `lIndex`  
 要返回的数组中的值的索引号。  
  
### <a name="return-value"></a>返回值  
 返回对所需的数组元素的引用。  
  
##  <a name="a-namegetcounta--ccomsafearraygetcount"></a><a name="getcount"></a>CComSafeArray::GetCount  
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
 与多维数组使用时，此方法将返回的特定维度中的元素的数目。  
  
##  <a name="a-namegetdimensionsa--ccomsafearraygetdimensions"></a><a name="getdimensions"></a>CComSafeArray::GetDimensions  
 返回数组中的维数。  
  
```
UINT GetDimensions() const;
```  
  
### <a name="return-value"></a>返回值  
 返回数组中的维数。  
  
##  <a name="a-namegetlowerbounda--ccomsafearraygetlowerbound"></a><a name="getlowerbound"></a>CComSafeArray::GetLowerBound  
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
 如果下限为 0，则表明其第一个元素是元素编号为 0 的类似 c 语言的数组。 如果出现错误，例如，维度无效参数，此方法调用`AtlThrow`与描述该错误的 HRESULT。  
  
##  <a name="a-namegetsafearrayptra--ccomsafearraygetsafearrayptr"></a><a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr  
 返回 `m_psa` 数据成员的地址。  
  
```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回一个指向[CComSafeArray::m_psa](#m_psa)数据成员。  
  
##  <a name="a-namegettypea--ccomsafearraygettype"></a><a name="gettype"></a>CComSafeArray::GetType  
 返回数组中存储的数据类型。  
  
```
VARTYPE GetType() const;
```  
  
### <a name="return-value"></a>返回值  
 返回存储在数组中，这可能是任何以下类型的数据类型︰  
  
|VARTYPE|说明|  
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
  
##  <a name="a-namegetupperbounda--ccomsafearraygetupperbound"></a><a name="getupperbound"></a>CComSafeArray::GetUpperBound  
 返回数组任意维度的上限。  
  
```
LONG GetUpperBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>参数  
 `uDim`  
 要为其获取上限的数组维度。 如果省略，默认值为 0。  
  
### <a name="return-value"></a>返回值  
 返回上限。 此值是包括在内，此维度的最大有效索引。  
  
### <a name="remarks"></a>备注  
 如果出现错误，例如，维度无效参数，此方法调用`AtlThrow`与描述该错误的 HRESULT。  
  
##  <a name="a-nameissizablea--ccomsafearrayissizable"></a><a name="issizable"></a>CComSafeArray::IsSizable  
 测试是否可重设 `CComSafeArray` 对象的大小。  
  
```
bool IsSizable() const;
```  
  
### <a name="return-value"></a>返回值  
 返回**true**如果`CComSafeArray`可调整**false**如果它不能。  
  
##  <a name="a-namempsaa--ccomsafearraympsa"></a><a name="m_psa"></a>CComSafeArray::m_psa  
 保留的地址**SAFEARRAY**访问的结构。  
  
```
LPSAFEARRAY m_psa;
```  
  
##  <a name="a-namemultidimgetata--ccomsafearraymultidimgetat"></a><a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt  
 从多维数组中检索单个元素。  
  
```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```  
  
### <a name="parameters"></a>参数  
 `alIndex`  
 对某个向量的每个维度的数组的索引的指针。 最左侧 （最不重要） 的维度是`alIndex`[0] *。*  
  
 *t*  
 对返回的数据的引用。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="a-namemultidimsetata--ccomsafearraymultidimsetat"></a><a name="multidimsetat"></a>CComSafeArray::MultiDimSetAt  
 设置多维数组中元素的值。  
  
```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```  
  
### <a name="parameters"></a>参数  
 `alIndex`  
 对某个向量的每个维度的数组的索引的指针。 最右边的 （最不重要） 维度是`alIndex`[0]。  
  
 *T*  
 指定新元素的值。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 这是多维版本[CComSafeArray::SetAt](#setat)。  
  
##  <a name="a-nameoperatorata--ccomsafearrayoperator-"></a><a name="operator_at"></a>CComSafeArray::operator\[\]  
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
 执行类似的功能为[CComSafeArray::GetAt](#getat)，但是，此运算符仅适用于一维数组。  
  
##  <a name="a-nameoperatoreqa--ccomsafearrayoperator-"></a><a name="operator_eq"></a>CComSafeArray::operator =  
 赋值运算符。  
  
```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>参数  
 `saSrc`  
 对 `CComSafeArray` 对象的引用。  
  
 `psaSrc`  
 一个指向**SAFEARRAY**对象。  
  
### <a name="return-value"></a>返回值  
 返回数组中存储的数据类型。  
  
##  <a name="a-nameoperatorlpsafearraya--ccomsafearrayoperator-lpsafearray"></a><a name="operator_lpsafearray"></a>CComSafeArray::operator LPSAFEARRAY  
 将值转换为 **SAFEARRAY** 指针。  
  
```
operator LPSAFEARRAY() const;
```  
  
### <a name="return-value"></a>返回值  
 将值转换为 **SAFEARRAY** 指针。  
  
##  <a name="a-nameresizea--ccomsafearrayresize"></a><a name="resize"></a>CComSafeArray::Resize  
 重设 `CComSafeArray` 对象的大小。  
  
```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>参数  
 `pBound`  
 一个指向**SAFEARRAYBOUND**结构，其中包含有关元素的数目和数组的下限。  
  
 `ulCount`  
 请求的已调整大小的数组中的对象数。  
  
 `lLBound`  
 下限。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 此方法仅调整大小最右边的维度。 它不会调整大小返回的数组**IsResizable**作为**false**。  
  
##  <a name="a-namesetata--ccomsafearraysetat"></a><a name="setat"></a>CComSafeArray::SetAt  
 设置一维数组中元素的值。  
  
```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lIndex`  
 若要设置的数组元素的索引号。  
  
 *t*  
 指定的元素的新值。  
  
 `bCopy`  
 指示是否应创建数据的副本。 默认值是**TRUE**。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 `bCopy`标志考虑在内时类型的元素`BSTR`或**VARIANT**添加到数组。 默认值为**TRUE**可确保在该元素已添加到数组时的数据创建一个新副本。  
  
## <a name="see-also"></a>另请参阅  
 [SAFEARRAY 数据类型](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e)   
 [CComSafeArray::Create](#create)   
 [CComSafeArray::Destroy](#destroy)   
 [类概述](../../atl/atl-class-overview.md)

