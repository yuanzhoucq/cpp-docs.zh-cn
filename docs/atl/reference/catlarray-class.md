---
title: "CAtlArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAtlArray
- ATL.CAtlArray
- CAtlArray
dev_langs:
- C++
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5fe987e428fc0dcf3e40bfb16aa26bcb90339aff
ms.lasthandoff: 02/24/2017

---
# <a name="catlarray-class"></a>CAtlArray 类
此类实现一个数组对象。  
  
## <a name="syntax"></a>语法  
  
```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```  
  
#### <a name="parameters"></a>参数  
 *E*  
 要存储在数组中的数据类型。  
  
 *ETraits*  
 用于复制或移动元素的代码。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[添加](#add)|调用此方法以将元素添加到数组对象。|  
|[追加](#append)|调用此方法以将一个数组的内容添加到另一个末尾。|  
|[AssertValid](#assertvalid)|调用此方法用于确认 array 对象有效。|  
|[CAtlArray](#catlarray)|构造函数。|  
|[~ CAtlArray](#dtor)|析构函数。|  
|[复制](#copy)|调用此方法将一个数组的元素复制到另一个。|  
|[FreeExtra](#freeextra)|调用此方法以从数组中移除任何空元素。|  
|[GetAt](#getat)|调用此方法从数组对象中检索单个元素。|  
|[GetCount](#getcount)|调用此方法可返回数组中存储的元素数量。|  
|[GetData](#getdata)|调用此方法以返回指向数组中的第一个元素的指针。|  
|[InsertArrayAt](#insertarrayat)|调用此方法要插入到另一个数组。|  
|[InsertAt](#insertat)|Array 对象调用此方法，以插入新元素 （或一个元素的多个副本）。|  
|[IsEmpty](#isempty)|调用此方法来测试如果数组为空。|  
|[RemoveAll](#removeall)|调用此方法以从数组对象中移除所有元素。|  
|[RemoveAt](#removeat)|调用此方法以从数组中移除一个或多个元素。|  
|[SetAt](#setat)|调用此方法以设置数组对象元素的值。|  
|[SetAtGrow](#setatgrow)|调用此方法以扩展所需的数组的数组对象中设置元素的值。|  
|[SetCount](#setcount)|调用此方法以设置数组对象的大小。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator&#91;&#93;](#operator_at)|调用此运算符可返回数组中的元素的引用。|  

  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[INARGTYPE](#inargtype)|要用于将元素添加到该数组的数据类型。|  
|[OUTARGTYPE](#outargtype)|要用于从数组中检索元素的数据类型。|  
  
## <a name="remarks"></a>备注  
 **CAtlArray**提供用于创建和管理的用户定义类型的元素数组的方法。 尽管类似于标准 C 数组、 **CAtlArray**可以动态地收缩对象并将其任意增大。 数组索引始终从开始位置 0，且的上限可固定的或允许扩展，如添加新元素。  
  
 对于只有少量元素，ATL 类数组[CSimpleArray](../../atl/reference/csimplearray-class.md)可用。  
  
 **CAtlArray**与 MFC 的密切相关**CArray**类，则正常在 MFC 项目中，虽然序列化支持。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="a-nameadda--catlarrayadd"></a><a name="add"></a>CAtlArray::Add  
 调用此方法以将元素添加到数组对象。  
  
```
size_t Add(INARGTYPE element);
size_t Add();
```  
  
### <a name="parameters"></a>参数  
 `element`  
 要添加到数组的元素。  
  
### <a name="return-value"></a>返回值  
 返回添加的元素的索引。  
  
### <a name="remarks"></a>备注  
 将新元素添加到数组末尾。 如果没有元素提供，添加一个空元素;它是数组增加大小，已添加的实际元素一样。 如果操作失败， [AtlThrow](http://msdn.microsoft.com/library/2bd111da-8170-488d-914a-c9bf6b6765f7)用参数 E_OUTOFMEMORY 调用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&1;](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]  
  
##  <a name="a-nameappenda--catlarrayappend"></a><a name="append"></a>CAtlArray::Append  
 调用此方法以将一个数组的内容添加到另一个末尾。  
  
```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>参数  
 `aSrc`  
 要追加的数组。  
  
### <a name="return-value"></a>返回值  
 返回第一个追加的元素的索引。  
  
### <a name="remarks"></a>备注  
 中提供的数组的元素添加到现有的数组的末尾。 如有必要，将分配内存以容纳新元素。  
  
 数组必须是相同的类型，而且不能将一个数组追加到其自身。  
  
 在调试生成中 ATLASSERT 如果将会引发`CAtlArray`参数不是有效的数组或如果`aSrc`指的是同一个对象。 在发布版本中，可能导致不可预知的行为的参数无效。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&2;](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]  
  
##  <a name="a-nameassertvalida--catlarrayassertvalid"></a><a name="assertvalid"></a>CAtlArray::AssertValid  
 调用此方法用于确认 array 对象有效。  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>备注  
 如果数组对象不是有效的`ATLASSERT`将引发断言。 此方法是定义 _DEBUG 时才可用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&3;](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]  
  
##  <a name="a-namecatlarraya--catlarraycatlarray"></a><a name="catlarray"></a>CAtlArray::CAtlArray  
 构造函数。  
  
```
CAtlArray() throw();
```  
  
### <a name="remarks"></a>备注  
 初始化数组对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&4;](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]  
  
##  <a name="a-namedtora--catlarraycatlarray"></a><a name="dtor"></a>CAtlArray:: ~ CAtlArray  
 析构函数。  
  
```
~CAtlArray() throw();
```  
  
### <a name="remarks"></a>备注  
 使用数组对象的任何资源将释放。  
  
##  <a name="a-namecopya--catlarraycopy"></a><a name="copy"></a>CAtlArray::Copy  
 调用此方法将一个数组的元素复制到另一个。  
  
```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>参数  
 `aSrc`  
 要复制到数组的元素的源。  
  
### <a name="remarks"></a>备注  
 调用此方法来覆盖一个数组的元素与另一个数组的元素。 如有必要，将分配内存以容纳新元素。 不能将一个数组的元素复制到本身。  
  
 如果要保留该数组的现有内容，请使用[CAtlArray::Append](#append)相反。  
  
 在调试生成中 ATLASSERT 如果将会引发现有`CAtlArray`对象不是有效的或者如果`aSrc`指的是同一个对象。 在发布版本中，可能导致不可预知的行为的参数无效。  
  
> [!NOTE]
> `CAtlArray::Copy`不支持使用创建的元素组成的数组[CAutoPtr](../../atl/reference/cautoptr-class.md)类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&5;](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]  
  
##  <a name="a-namefreeextraa--catlarrayfreeextra"></a><a name="freeextra"></a>CAtlArray::FreeExtra  
 调用此方法以从数组中移除任何空元素。  
  
```
void FreeExtra() throw();
```  
  
### <a name="remarks"></a>备注  
 将删除任何空元素，但大小和数组的上限将保持不变。  
  
 在调试版本中，将引发 ATLASSERT 如果 CAtlArray 对象不是有效的或者如果数组会超出其最大大小。  
  
##  <a name="a-namegetata--catlarraygetat"></a><a name="getat"></a>CAtlArray::GetAt  
 调用此方法从数组对象中检索单个元素。  
  
```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```  
  
### <a name="parameters"></a>参数  
 `iElement`  
 要返回的数组元素的索引值。  
  
### <a name="return-value"></a>返回值  
 返回对所需的数组元素的引用。  
  
### <a name="remarks"></a>备注  
 在调试生成中 ATLASSERT 如果将会引发`iElement`超过数组中的元素数。 在发布版本中，无效的参数可能会导致不可预知的行为。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&6;](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]  
  
##  <a name="a-namegetcounta--catlarraygetcount"></a><a name="getcount"></a>CAtlArray::GetCount  
 调用此方法可返回数组中存储的元素数量。  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回存储在数组中的元素数量。  
  
### <a name="remarks"></a>备注  
 返回的值在数组中的第一个元素位于位置 0，如`GetCount`始终为 1 大于最大的索引。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlArray::GetAt](#getat)。  
  
##  <a name="a-namegetdataa--catlarraygetdata"></a><a name="getdata"></a>CAtlArray::GetData  
 调用此方法以返回指向数组中的第一个元素的指针。  
  
```
E* GetData() throw();
const E* GetData() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回指向数组中存储的第一个元素的内存位置的指针。 如果不有任何元素，则返回 NULL。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&7;](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]  
  
##  <a name="a-nameinargtypea--catlarrayinargtype"></a><a name="inargtype"></a>CAtlArray::INARGTYPE  
 要用于将元素添加到该数组的数据类型。  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="a-nameinsertarrayata--catlarrayinsertarrayat"></a><a name="insertarrayat"></a>CAtlArray::InsertArrayAt  
 调用此方法要插入到另一个数组。  
  
```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```  
  
### <a name="parameters"></a>参数  
 `iStart`  
 从该处的数组是要插入的索引。  
  
 `paNew`  
 要插入的数组。  
  
### <a name="remarks"></a>备注  
 数组的元素`paNew`复制到开始元素处的数组对象`iStart`。 现有的数组元素会移动以避免被覆盖。  
  
 在调试生成中 ATLASSERT 如果将会引发`CAtlArray`对象不是有效的或者如果`paNew`指针为 NULL 或无效。  
  
> [!NOTE]
> `CAtlArray::InsertArrayAt`不支持使用创建的元素组成的数组[CAutoPtr](../../atl/reference/cautoptr-class.md)类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&8;](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]  
  
##  <a name="a-nameinsertata--catlarrayinsertat"></a><a name="insertat"></a>CAtlArray::InsertAt  
 Array 对象调用此方法，以插入新元素 （或一个元素的多个副本）。  
  
```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```  
  
### <a name="parameters"></a>参数  
 `iElement`  
 元素的位置插入索引。  
  
 `element`  
 要插入的元素的值。  
  
 `nCount`  
 要添加的元素数。  
  
### <a name="remarks"></a>备注  
 将一个或多个元素插入到数组，从索引处开始`iElement`。 现有元素会移动以避免被覆盖。  
  
 在调试生成中 ATLASSERT 如果将会引发`CAtlArray`对象无效，要添加的元素数为零，或者组合的元素数的数组以包含太大。 在零售版本中传递了无效参数可能会导致不可预知的结果。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&9;](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]  
  
##  <a name="a-nameisemptya--catlarrayisempty"></a><a name="isempty"></a>CAtlArray::IsEmpty  
 调用此方法来测试如果数组为空。  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果数组为空，则返回 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 数组是认为如果它不包含任何元素为空。 因此，即使该数组包含空元素，它不为空。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&10;](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]  
  
##  <a name="a-nameoperatorata--catlarrayoperator-"></a><a name="operator_at"></a>CAtlArray::operator]  
 调用此运算符可返回数组中的元素的引用。  
  
```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```  
  
### <a name="parameters"></a>参数  
 `iElement`  
 要返回的数组元素的索引值。  
  
### <a name="return-value"></a>返回值  
 返回对所需的数组元素的引用。  
  
### <a name="remarks"></a>备注  
 执行类似的功能为[CAtlArray::GetAt](#getat)。 与 MFC 类不同[CArray](../../mfc/reference/carray-class.md)，此运算符不能用作替代[CAtlArray::SetAt](#setat)。  
  
 在调试生成中 ATLASSERT 如果将会引发`iElement`超出数组中元素的总数。 在零售版本中无效的参数可能会导致不可预知的结果。  
  
##  <a name="a-nameoutargtypea--catlarrayoutargtype"></a><a name="outargtype"></a>CAtlArray::OUTARGTYPE  
 要用于从数组中检索元素的数据类型。  
  
```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```  
  
##  <a name="a-nameremovealla--catlarrayremoveall"></a><a name="removeall"></a>CAtlArray::RemoveAll  
 调用此方法以从数组对象中移除所有元素。  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>备注  
 删除数组对象中的所有元素。  
  
 此方法调用[CAtlArray::SetCount](#setcount)来调整数组的大小，并随后释放任何已分配的内存。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlArray::IsEmpty](#isempty)。  
  
##  <a name="a-nameremoveata--catlarrayremoveat"></a><a name="removeat"></a>CAtlArray::RemoveAt  
 调用此方法以从数组中移除一个或多个元素。  
  
```
void RemoveAt(size_t iElement, size_t nCount = 1);
```  
  
### <a name="parameters"></a>参数  
 `iElement`  
 要移除的第一个元素的索引。  
  
 `nCount`  
 要移除的元素数。  
  
### <a name="remarks"></a>备注  
 从数组中移除一个或多个元素。 剩余的所有元素都向下都移动。 上限是递减，但之前对的调用，不释放内存[CAtlArray::FreeExtra](#freeextra)进行。  
  
 在调试生成中 ATLASSERT 如果将会引发`CAtlArray`对象不是有效的或者，如果总和`iElement`和`nCount`超出数组中元素的总数。 在零售版本中无效的参数可能会导致不可预知的结果。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&11;](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]  
  
##  <a name="a-namesetata--catlarraysetat"></a><a name="setat"></a>CAtlArray::SetAt  
 调用此方法以设置数组对象元素的值。  
  
```
void SetAt(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>参数  
 `iElement`  
 指向要设置的数组元素的索引。  
  
 `element`  
 指定的元素的新值。  
  
### <a name="remarks"></a>备注  
 在调试生成中 ATLASSERT 如果将会引发`iElement`超过数组中的元素数。 在零售版本中无效的参数可能会导致不可预知的结果。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlArray::GetAt](#getat)。  
  
##  <a name="a-namesetcounta--catlarraysetcount"></a><a name="setcount"></a>CAtlArray::SetCount  
 调用此方法以设置数组对象的大小。  
  
```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```  
  
### <a name="parameters"></a>参数  
 `nNewSize`  
 数组所需的大小。  
  
 `nGrowBy`  
 用来确定的值使缓冲区的大小。 值为-1 会导致要使用的内部计算的值。  
  
### <a name="return-value"></a>返回值  
 如果数组否则是已成功地调整大小，则返回 false，则返回 true。  
  
### <a name="remarks"></a>备注  
 数组可以增加或减少的大小。 如果增加，额外的空元素已添加到数组中。 如果减小时，将删除具有最大索引的元素，并释放内存。  
  
 此方法用于在使用它之前设置数组的大小。 如果`SetCount`没用，添加元素的过程-执行后续的内存分配和 — 将降低性能，并产生内存碎片。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlArray::GetData](#getdata)。  
  
##  <a name="a-namesetatgrowa--catlarraysetatgrow"></a><a name="setatgrow"></a>CAtlArray::SetAtGrow  
 调用此方法以扩展所需的数组的数组对象中设置元素的值。  
  
```
void SetAtGrow(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>参数  
 `iElement`  
 指向要设置的数组元素的索引。  
  
 `element`  
 指定的元素的新值。  
  
### <a name="remarks"></a>备注  
 替换由索引指向的元素的值。 如果`iElement`大于当前大小的数组，数组自动增大调用[CAtlArray::SetCount](#setcount)。 在调试生成中 ATLASSERT 如果将会引发`CAtlArray`对象无效。 在零售版本中无效的参数可能会导致不可预知的结果。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&12;](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MMXSwarm 示例](../../visual-cpp-samples.md)   
 [DynamicConsumer 示例](../../visual-cpp-samples.md)   
 [UpdatePV 示例](../../visual-cpp-samples.md)   
 [字幕示例](../../visual-cpp-samples.md)   
 [CArray 类](../../mfc/reference/carray-class.md)   
 [类概述](../../atl/atl-class-overview.md)

