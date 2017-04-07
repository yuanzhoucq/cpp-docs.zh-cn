---
title: "CArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- CArray class
- arrays [C++], classes
- templates, collection classes
- collection classes, template-based
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
caps.latest.revision: 33
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
ms.openlocfilehash: bac8e08540ffead565d1097c6ef1efcae5e606c2
ms.lasthandoff: 02/24/2017

---
# <a name="carray-class"></a>CArray 类
支持类似于 C 数组、 但可以动态减小和增大的根据需要的数组。  
  
## <a name="syntax"></a>语法  
  
```  
template <class TYPE, class ARG_TYPE = const TYPE&>  
class CArray : public CObject  
```  
  
#### <a name="parameters"></a>参数  
 `TYPE`  
 指定数组中存储的对象类型的模板参数。 `TYPE`是一个参数，返回的`CArray`。  
  
 `ARG` *_* `TYPE`  
 指定用于访问存储在数组中的对象的参数类型的模板参数。 通常引用`TYPE`。 `ARG_TYPE`是一个参数，传递给`CArray`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CArray::CArray](#carray)|构造一个空数组。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CArray::Add](#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|  
|[Carray:: Append](#append)|将另一个数组追加到数组中;如果需要，扩展该数组|  
|[Carray:: Copy](#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|  
|[CArray::ElementAt](#elementat)|在该数组中返回对元素指针的临时引用。|  
|[CArray::FreeExtra](#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|  
|[CArray::GetAt](#getat)|返回给定索引位置处的值。|  
|[CArray::GetCount](#getcount)|获取此数组中的元素数。|  
|[CArray::GetData](#getdata)|允许访问该数组中的元素。 可以是**NULL**。|  
|[CArray::GetSize](#getsize)|获取此数组中的元素数。|  
|[CArray::GetUpperBound](#getupperbound)|返回最大的有效索引。|  
|[CArray::InsertAt](#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|  
|[CArray::IsEmpty](#isempty)|确定数组是否为空。|  
|[CArray::RemoveAll](#removeall)|从此数组中移除所有元素。|  
|[CArray::RemoveAt](#removeat)|移除特定索引处的元素。|  
|[CArray::SetAt](#setat)|设置给定索引的值；不允许对该数组进行扩展。|  
|[CArray::SetAtGrow](#setatgrow)|设置给定索引的值；根据需要扩展该数组。|  
|[CArray::SetSize](#setsize)|设置要在该数组中包含的元素数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[operator[]](#operator_at)|设置或获取位于指定索引处的元素。|  
  
## <a name="remarks"></a>备注  
 数组索引始终位置 0 处开始。 您可以决定是修复上限还是启用要展开时添加过去的当前绑定元素的数组。 内存是连续分配的上限，即使某些元素均为 null。  
  
> [!NOTE]
>  调整大小的大多数方法`CArray`对象，或将添加到该元素使用[memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)要从中移动元素。 这是一个问题，因为`memcpy_s`不符合要求的构造函数要调用的任何对象。 如果中的项`CArray`互不兼容`memcpy_s`，您必须创建一个新`CArray`的适当的大小。 然后，您必须使用[carray:: Copy](#copy)和[CArray::SetAt](#setat)用于填充新的数组，因为这些方法使用而不是赋值运算符`memcpy_s`。  
  
 C 数组、 访问的时间与`CArray`索引的元素是常量，它独立于数组大小。  
  
> [!TIP]
>  在使用一个数组之前, 使用[SetSize](#setsize)建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。  
  
 如果你需要在数组中的各个元素的转储，则必须设置的深度[CDumpContext](../../mfc/reference/cdumpcontext-class.md)为 1 或更大的对象。  
  
 此类调用全局帮助器函数的某些成员函数必须进行自定义的大部分使用`CArray`类。 请参阅主题[集合类帮助器](../../mfc/reference/collection-class-helpers.md)MFC 宏和全局部分中。  
  
 数组类派生就像列表派生。  
  
 有关如何使用`CArray`，请参阅文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CArray`  
  
## <a name="requirements"></a>要求  
 `Header:`afxtempl.h  
  
##  <a name="add"></a>CArray::Add  
 将新元素添加到数组，由 1 增长数组的末尾。  
  
```  
INT_PTR Add(ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 `ARG_TYPE`  
 指定引用此数组中的元素的参数的类型的模板参数。  
  
 `newElement`  
 要添加到该数组的元素。  
  
### <a name="return-value"></a>返回值  
 添加的元素的索引。  
  
### <a name="remarks"></a>备注  
 如果[SetSize](#setsize)已经用于与`nGrowBy`可能分配值大于 1，则额外的内存。 但是，上限将增加仅为 1。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&22;](../../mfc/codesnippet/cpp/carray-class_1.cpp)]  
  
##  <a name="append"></a>Carray:: Append  
 调用该成员函数以将一个数组的内容添加到另一个末尾。  
  
```  
INT_PTR Append(const CArray& src);
```  
  
### <a name="parameters"></a>参数  
 *src*  
 要追加到一个数组的元素的源。  
  
### <a name="return-value"></a>返回值  
 第一个追加的元素的索引。  
  
### <a name="remarks"></a>备注  
 数组必须是类型的相同。  
  
 如有必要，**追加**可能会分配额外的内存来容纳追加到该数组的元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections 第&23;](../../mfc/codesnippet/cpp/carray-class_2.cpp)]  
  
##  <a name="carray"></a>CArray::CArray  
 构造一个空数组。  
  
```  
CArray();
```  
  
### <a name="remarks"></a>备注  
 数组增长一次一个元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&24;](../../mfc/codesnippet/cpp/carray-class_3.cpp)]  
  
##  <a name="copy"></a>Carray:: Copy  
 使用此成员函数将一个数组的元素复制到另一个。  
  
```  
void Copy(const CArray& src);
```  
  
### <a name="parameters"></a>参数  
 *src*  
 要复制到数组的元素的源。  
  
### <a name="remarks"></a>备注  
 调用该成员函数以使用另一数组元素覆盖一个数组的元素。  
  
 **复制**不会释放内存; 但是，如有必要，**副本**可能会分配额外的内存来容纳的元素复制到数组。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&25;](../../mfc/codesnippet/cpp/carray-class_4.cpp)]  
  
##  <a name="elementat"></a>CArray::ElementAt  
 返回对指定的元素，该数组中的临时引用。  
  
```  
TYPE& ElementAt(INT_PTR nIndex);  
const TYPE& ElementAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 一个大于或等于 0 的整数索引且小于或等于返回的值[GetUpperBound](#getupperbound)。  
  
### <a name="return-value"></a>返回值  
 对数组元素的引用。  
  
### <a name="remarks"></a>备注  
 它用于实现数组左侧赋值运算符。  
  
### <a name="example"></a>示例  
  请参阅示例[GetSize](#getsize)。  
  
##  <a name="freeextra"></a>CArray::FreeExtra  
 释放任何额外的内存，已分配，而增长数组。  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>备注  
 此函数具有对该数组的上限的大小没有影响。  
  
### <a name="example"></a>示例  
  请参阅示例[GetData](#getdata)。  
  
##  <a name="getat"></a>CArray::GetAt  
 返回指定索引处的数组元素。  
  
```  
TYPE& GetAt(INT_PTR nIndex);  
const TYPE& GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定的数组元素的类型的模板参数。  
  
 `nIndex`  
 一个大于或等于 0 的整数索引且小于或等于返回的值[GetUpperBound](#getupperbound)。  
  
### <a name="return-value"></a>返回值  
 当前位于此索引的数组元素。  
  
### <a name="remarks"></a>备注  
 传递值为负或值返回的值大于`GetUpperBound`将导致失败的断言。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&26;](../../mfc/codesnippet/cpp/carray-class_5.cpp)]  
  
##  <a name="getcount"></a>CArray::GetCount  
 返回数组元素的个数。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 数组中的项数。  
  
### <a name="remarks"></a>备注  
 调用此方法来检索数组中的元素数。 因为索引是从零开始的则大小将为 1 大于最大的索引。 调用此方法将生成相同的结果[CArray::GetSize](#getsize)方法。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&27;](../../mfc/codesnippet/cpp/carray-class_6.cpp)]  
  
##  <a name="getdata"></a>CArray::GetData  
 使用此成员函数来获取对数组中元素的直接访问。  
  
```  
const TYPE* GetData() const; 
TYPE* GetData();
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 指定的数组元素的类型的模板参数。  
  
### <a name="return-value"></a>返回值  
 指向数组元素的指针。  
  
### <a name="remarks"></a>备注  
 如果没有元素可用，`GetData`返回 null 值。  
  
 尽管对数组的元素的直接访问可以帮助您更快地工作时, 要格外小心调用`GetData`; 直接进行的任何错误会影响您的数组的元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&28;](../../mfc/codesnippet/cpp/carray-class_7.cpp)]  
  
##  <a name="getsize"></a>CArray::GetSize  
 返回数组的大小。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>备注  
 因为索引是从零开始的则大小将为 1 大于最大的索引。 调用此方法将生成相同的结果[CArray::GetCount](#getcount)方法。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&29;](../../mfc/codesnippet/cpp/carray-class_8.cpp)]  
  
##  <a name="getupperbound"></a>CArray::GetUpperBound  
 返回此数组中的当前的上限。  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="remarks"></a>备注  
 数组索引是从零开始的因为此函数返回值 1 小于`GetSize`。  
  
 条件**GetUpperBound （)** =-1 指示该数组包含任何元素。  
  
### <a name="example"></a>示例  
  请参阅示例[CArray::GetAt](#getat)。  
  
##  <a name="insertat"></a>CArray::InsertAt  
 第一个版本`InsertAt`中数组的指定索引处插入一个元素 （或一个元素的多个副本）。  
  
```  
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,  
    INT_PTR nCount = 1);
 
void InsertAt(
    INT_PTR nStartIndex,  
    CArray* pNewArray);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 可能会高于返回的值的整数索引`GetUpperBound`。  
  
 `ARG_TYPE`  
 此数组中指定的元素的类型的模板参数。  
  
 `newElement`  
 要放置在此数组的元素。  
  
 `nCount`  
 此元素应为次数插入 （默认值为 1）。  
  
 `nStartIndex`  
 可能会高于返回的值的整数索引[GetUpperBound](#getupperbound)。  
  
 `pNewArray`  
 另一个数组，其中包含要添加到该数组的元素。  
  
### <a name="remarks"></a>备注  
 在过程中，它上移 （通过递增索引） 在此索引和它现有的元素上移它上面的所有元素。  
  
 第二个版本的所有元素都插入从另一个`CArray`集合中，从开始`nStartIndex`位置。  
  
 `SetAt`函数时，与此相反，替换一个指定的数组元素并不移动任何元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&30;](../../mfc/codesnippet/cpp/carray-class_9.cpp)]  
  
##  <a name="isempty"></a>CArray::IsEmpty  
 确定数组是否为空。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果数组不包含任何元素，则非零值否则为 0。  
  
##  <a name="operator_at"></a>CArray::operator\[\]  
 这些下标运算符是一个方便替换[SetAt](#setat)和[GetAt](#getat)函数。  
  
```  
TYPE& operator[](int_ptr nindex);  
const TYPE& operator[](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 此数组中指定的元素的类型的模板参数。  
  
 `nIndex`  
 要访问的元素的索引。  
  
### <a name="remarks"></a>备注  
 在第一个操作数为数组不调用**const**，可以在赋值语句的左侧 （左值） 或右侧 （右值） 一起使用。 第二个名为**const**数组，可能会使用仅在右侧。  
  
 库的调试版本断言下标 （无论在左侧或右侧赋值语句的内容） 是否超出界限。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&34;](../../mfc/codesnippet/cpp/carray-class_10.cpp)]  
  
##  <a name="relocateelements"></a>CArray::RelocateElements  
 将数据重新调整到一个新的缓冲区数组应增大或收缩时。  
  
```  
template<class TYPE, class ARG_TYPE>  
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,  
    const TYPE* pData,  
    INT_PTR nCount);
```  
  
### <a name="parameters"></a>参数  
 `pNewData`  
 新的缓冲区的数组元素的数组。  
  
 `pData`  
 旧元素的数组。  
  
 `nCount`  
 旧的数组中的元素数。  
  
### <a name="remarks"></a>备注  
 `pNewData`始终是足以容纳所有`pData`元素。  
  
 [CArray](../../mfc/reference/carray-class.md)实现使用此方法将旧的数据复制到新的缓冲区，该数组应增大或收缩时 (当[SetSize](#setsize)或[FreeExtra](#freeextra)称为)。 默认实现只是复制的数据。  
  
 对于在其中一个元素包含一个指向一个成员，或另一种结构包含指向一个数组元素的指针的数组，指针不会更新纯副本中。 在这种情况下，您可以通过实现的专用化来更正指针`RelocateElements`与相关的类型。 您还有负责数据复制。  
  
##  <a name="removeall"></a>CArray::RemoveAll  
 从此数组中移除所有元素。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 如果已经为空数组，该函数仍然起作用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&31;](../../mfc/codesnippet/cpp/carray-class_11.cpp)]  
  
##  <a name="removeat"></a>CArray::RemoveAt  
 移除数组中指定索引处开始的一个或多个元素。  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 一个大于或等于 0 的整数索引且小于或等于返回的值[GetUpperBound](#getupperbound)。  
  
 `nCount`  
 要移除的元素数。  
  
### <a name="remarks"></a>备注  
 在过程中，移向下上面已移除元素的所有元素。 它递减上限绑定的数组，但不会释放内存。  
  
 如果您尝试删除不是删除点上方的数组中包含的多个元素，然后断言库的调试版本。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&32;](../../mfc/codesnippet/cpp/carray-class_12.cpp)]  
  
##  <a name="setat"></a>CArray::SetAt  
 设置指定索引处的数组元素。  
  
```  
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 一个大于或等于 0 的整数索引且小于或等于返回的值[GetUpperBound](#getupperbound)。  
  
 `ARG_TYPE`  
 指定用于引用数组元素的参数的类型的模板参数。  
  
 `newElement`  
 要存储在指定位置的新元素值。  
  
### <a name="remarks"></a>备注  
 `SetAt`不会导致要增长的数组。 使用[SetAtGrow](#setatgrow)如果您想要自动增长的数组。  
  
 您必须确保您的索引值表示数组中的有效位置。 如果该值超出界限，库的调试版本断言。  
  
### <a name="example"></a>示例  
  请参阅示例[GetAt](#getat)。  
  
##  <a name="setatgrow"></a>CArray::SetAtGrow  
 设置指定索引处的数组元素。  
  
```  
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 一个大于或等于 0 的整数索引。  
  
 `ARG_TYPE`  
 数组中指定的元素的类型的模板参数。  
  
 `newElement`  
 要添加到该数组的元素。 一个**NULL**允许值。  
  
### <a name="remarks"></a>备注  
 根据需要自动扩展该数组 （即，上限为进行调整以容纳新元素）。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections 第&33;](../../mfc/codesnippet/cpp/carray-class_13.cpp)]  
  
##  <a name="setsize"></a>CArray::SetSize  
 建立一个空的或现有的数组; 的大小如有必要，请分配内存。  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>参数  
 `nNewSize`  
 新的数组大小 （多个元素） 中。 必须是大于或等于 0。  
  
 `nGrowBy`  
 要分配的大小增长是否需要的元素插槽最少次数。  
  
### <a name="remarks"></a>备注  
 如果新的大小小于旧的大小，则数组将被截断并释放所有未使用的内存。  
  
 使用此函数在开始使用数组之前设置数组的大小。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。  
  
 `nGrowBy`参数会影响内部内存分配，而增长数组。 它使用永远不会影响数组大小由报告[GetSize](#getsize)和[GetUpperBound](#getupperbound)。 如果使用默认值，则 MFC 将通过计算来避免内存碎片并优化其在大多数情况下的效率的方式的内存分配。  
  
### <a name="example"></a>示例  
  请参阅示例[GetData](#getdata)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例收集](../../visual-cpp-samples.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CObArray 类](../../mfc/reference/cobarray-class.md)   
 [集合类帮助器](../../mfc/reference/collection-class-helpers.md)

