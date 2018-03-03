---
title: "CArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
- CPP
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85e7bf9518ad96e5a67f2d19d3729e5813d3f84d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="carray-class"></a>CArray 类
支持类似于 C 数组，但可以动态减小和增大根据需要的数组。  
  
## <a name="syntax"></a>语法  
  
```  
template <class TYPE, class ARG_TYPE = const TYPE&>  
class CArray : public CObject  
```  
  
#### <a name="parameters"></a>参数  
 `TYPE`  
 指定数组中存储的对象类型的模板参数。 `TYPE`是一个参数，返回`CArray`。  
  
 `ARG` *_* `TYPE`  
 指定用于访问存储在数组中对象的自变量类型的模板参数。 通常对的引用`TYPE`。 `ARG_TYPE`是传递给参数`CArray`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CArray::CArray](#carray)|构造一个空数组。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CArray::Add](#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|  
|[Carray:: Append](#append)|将另一个数组追加到数组中;如有必要，请扩展该数组|  
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
  
|名称|描述|  
|----------|-----------------|  
|[operator[]](#operator_at)|设置或获取位于指定索引处的元素。|  
  
## <a name="remarks"></a>备注  
 数组索引始终在位置 0 处启动。 你可以决定是否以修复上限或启用要展开时添加过去的当前绑定元素的数组。 内存分配连续给上限，即使某些元素为 null。  
  
> [!NOTE]
>  调整大小的大多数方法`CArray`对象或添加到它的元素使用[memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)移动元素。 这是一个问题，因为`memcpy_s`与任何需要的构造函数要调用的对象不兼容。 如果中的项`CArray`与不兼容`memcpy_s`，你必须创建一个新`CArray`的适当的大小。 然后，你必须使用[carray:: Copy](#copy)和[CArray::SetAt](#setat)用于填充该新数组，因为这些方法使用而不是赋值运算符`memcpy_s`。  
  
 C 数组，访问时间与`CArray`索引的元素是常数，它独立于数组大小。  
  
> [!TIP]
>  在使用数组之前, 使用[SetSize](#setsize)建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。  
  
 如果你需要在一个数组中的各个元素的转储，则必须设置的深度[CDumpContext](../../mfc/reference/cdumpcontext-class.md)到 1 或更大的对象。  
  
 全局帮助器函数，此类调用某些成员函数必须进行自定义的大部分使用`CArray`类。 请参阅主题[集合类帮助器](../../mfc/reference/collection-class-helpers.md)MFC 宏和全局函数部分中。  
  
 数组类派生就像列表派生。  
  
 有关如何使用`CArray`，请参阅文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CArray`  
  
## <a name="requirements"></a>惠?  
 `Header:`afxtempl.h  
  
##  <a name="add"></a>CArray::Add  
 将新元素添加到数组中，按 1 增长数组的末尾。  
  
```  
INT_PTR Add(ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 `ARG_TYPE`  
 模板参数来指定自变量引用此数组中的元素的类型。  
  
 `newElement`  
 要添加到该数组的元素。  
  
### <a name="return-value"></a>返回值  
 添加元素的索引。  
  
### <a name="remarks"></a>备注  
 如果[SetSize](#setsize)已用于`nGrowBy`可能分配值大于 1，则额外的内存。 但是，上限将增加仅为 1。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]  
  
##  <a name="append"></a>Carray:: Append  
 调用此成员函数可将一个数组的内容添加到另一个末尾。  
  
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
  
 如有必要，**追加**可能会分配额外内存来容纳追加到该数组的元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]  
  
##  <a name="carray"></a>CArray::CArray  
 构造一个空数组。  
  
```  
CArray();
```  
  
### <a name="remarks"></a>备注  
 数组增长一次一个元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]  
  
##  <a name="copy"></a>Carray:: Copy  
 使用此成员函数将一个数组的元素复制到另一个。  
  
```  
void Copy(const CArray& src);
```  
  
### <a name="parameters"></a>参数  
 *src*  
 要复制到数组的元素的源。  
  
### <a name="remarks"></a>备注  
 调用此成员函数以覆盖与另一个数组的元素的一个数组的元素。  
  
 **复制**不释放内存; 但是，如有必要，**复制**可能会分配额外内存来容纳的元素复制到数组。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]  
  
##  <a name="elementat"></a>CArray::ElementAt  
 返回到该数组中指定的元素的临时引用。  
  
```  
TYPE& ElementAt(INT_PTR nIndex);  
const TYPE& ElementAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 整数索引大于或等于 0 且小于或等于返回的值[GetUpperBound](#getupperbound)。  
  
### <a name="return-value"></a>返回值  
 对数组元素的引用。  
  
### <a name="remarks"></a>备注  
 它用于实现数组左侧赋值运算符。  
  
### <a name="example"></a>示例  
  请参阅示例[GetSize](#getsize)。  
  
##  <a name="freeextra"></a>CArray::FreeExtra  
 释放任何额外已分配内存，而数组已增长。  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>备注  
 此函数不起的大小或数组的上限。  
  
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
 整数索引大于或等于 0 且小于或等于返回的值[GetUpperBound](#getupperbound)。  
  
### <a name="return-value"></a>返回值  
 当前位于此索引的数组元素。  
  
### <a name="remarks"></a>备注  
 传递值为负或值返回的值大于`GetUpperBound`将导致失败的断言。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]  
  
##  <a name="getcount"></a>CArray::GetCount  
 返回数组元素的数目。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 数组中的项数。  
  
### <a name="remarks"></a>备注  
 调用此方法来检索其中的数组中的元素数。 因为索引是从零开始，大小为 1 大于最大的索引。 调用此方法将生成与相同的结果[CArray::GetSize](#getsize)方法。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]  
  
##  <a name="getdata"></a>CArray::GetData  
 使用此成员函数来获取数组中的元素的直接访问。  
  
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
 如果没有元素可用，`GetData`返回一个 null 值。  
  
 对数组的元素的直接访问可帮助你更快地工作，而时要格外小心调用`GetData`; 直接进行的任何错误会影响你数组的元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]  
  
##  <a name="getsize"></a>CArray::GetSize  
 返回数组的大小。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>备注  
 因为索引是从零开始，大小为 1 大于最大的索引。 调用此方法将生成与相同的结果[CArray::GetCount](#getcount)方法。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]  
  
##  <a name="getupperbound"></a>CArray::GetUpperBound  
 返回此数组中的当前的上限。  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="remarks"></a>备注  
 数组索引是从零开始的因为此函数将返回值 1 小于`GetSize`。  
  
 条件**GetUpperBound （)** =-1 指示该数组包含任何元素。  
  
### <a name="example"></a>示例  
  请参阅示例[CArray::GetAt](#getat)。  
  
##  <a name="insertat"></a>CArray::InsertAt  
 第一个版本`InsertAt`中数组的指定索引处插入一个元素 （或多个元素的副本）。  
  
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
 可能返回的值大于整数索引`GetUpperBound`。  
  
 `ARG_TYPE`  
 在此数组中指定的元素类型的模板参数。  
  
 `newElement`  
 要放置在此数组的元素。  
  
 `nCount`  
 此元素应为次数插入 （默认为 1）。  
  
 `nStartIndex`  
 可能返回的值大于整数索引[GetUpperBound](#getupperbound)。  
  
 `pNewArray`  
 包含要添加到该数组的元素的另一个数组。  
  
### <a name="remarks"></a>备注  
 在过程中，它上移 （通过将递增索引） 在此索引，和它的现有元素上移它上面的所有元素。  
  
 第二个版本将所有元素都插入从另一个`CArray`从开始的集合`nStartIndex`位置。  
  
 `SetAt`函数，与此相反，替换一个指定的数组元素和任何元素不移位。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]  
  
##  <a name="isempty"></a>CArray::IsEmpty  
 确定数组是否为空。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果数组不包含任何元素; 则为非 0否则为 0。  
  
##  <a name="operator_at"></a>CArray::operator\[\]  
 这些下标运算符是一个方便替换[SetAt](#setat)和[GetAt](#getat)函数。  
  
```  
TYPE& operator[](int_ptr nindex);  
const TYPE& operator[](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 在此数组中指定的元素类型的模板参数。  
  
 `nIndex`  
 若要访问的元素的索引。  
  
### <a name="remarks"></a>备注  
 第一个运算符，为不数组调用**const**，可以在右侧 （右值） 或赋值语句的左侧 （左值） 一起使用。 第二个，为调用**const**数组，可能使用仅在右侧。  
  
 库的调试版本断言下标 （或者在左侧或赋值语句右侧） 是否超出界限。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]  
  
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
 一个新的缓冲区中的元素数组。  
  
 `pData`  
 旧元素的数组。  
  
 `nCount`  
 旧的数组中的元素数目。  
  
### <a name="remarks"></a>备注  
 `pNewData`始终是足够大以保存所有`pData`元素。  
  
 [CArray](../../mfc/reference/carray-class.md)实现使用此方法将旧的数据复制到新的缓冲区，数组应增大或收缩时 (当[SetSize](#setsize)或[FreeExtra](#freeextra)称为)。 默认实现只需复制的数据。  
  
 对于在其中元素包含一个自己的成员的指针或另一种结构包含一个数组元素的指针的数组，指针不会更新纯副本中。 在这种情况下，可以通过实现的专用化更正指针`RelocateElements`与相关的类型。 你负责还复制数据。  
  
##  <a name="removeall"></a>CArray::RemoveAll  
 从此数组中移除所有元素。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 如果已经为空数组，该函数仍然正常工作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]  
  
##  <a name="removeat"></a>CArray::RemoveAt  
 移除数组中指定索引处开始的一个或多个元素。  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 整数索引大于或等于 0 且小于或等于返回的值[GetUpperBound](#getupperbound)。  
  
 `nCount`  
 要移除的元素数。  
  
### <a name="remarks"></a>备注  
 在过程中，它会转而下上面已移除元素的所有元素。 它递减上限绑定的数组，但不释放内存。  
  
 如果你尝试删除不是删除点上方数组中包含的多个元素，然后断言库的调试版本。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]  
  
##  <a name="setat"></a>CArray::SetAt  
 设置指定索引处的数组元素。  
  
```  
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 整数索引大于或等于 0 且小于或等于返回的值[GetUpperBound](#getupperbound)。  
  
 `ARG_TYPE`  
 模板参数来指定自变量用于引用数组元素的类型。  
  
 `newElement`  
 要存储在指定位置的新元素值。  
  
### <a name="remarks"></a>备注  
 `SetAt`不会导致要增长的数组。 使用[SetAtGrow](#setatgrow)如果你想要自动增长的数组。  
  
 你必须确保你的索引值表示数组中的有效位置。 如果该值超出界限，库的调试版本断言。  
  
### <a name="example"></a>示例  
  请参阅示例[GetAt](#getat)。  
  
##  <a name="setatgrow"></a>CArray::SetAtGrow  
 设置指定索引处的数组元素。  
  
```  
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 大于或等于 0 的整数索引。  
  
 `ARG_TYPE`  
 数组中指定的元素类型的模板参数。  
  
 `newElement`  
 要添加到该数组的元素。 A **NULL**允许值。  
  
### <a name="remarks"></a>备注  
 数组是自动增长如有必要 （即，上限调整以容纳新元素）。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]  
  
##  <a name="setsize"></a>CArray::SetSize  
 建立一个空的或现有的数组; 的大小如有必要，请分配内存。  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>参数  
 `nNewSize`  
 新数组大小 （即元素的数目）。 必须大于或等于 0。  
  
 `nGrowBy`  
 要分配如果大小增加是必需的元素插槽中最小的数。  
  
### <a name="remarks"></a>备注  
 如果新的大小小于旧大小，然后数组将被截断并释放所有未使用的内存。  
  
 使用此函数在开始使用数组之前设置你的数组的大小。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。  
  
 `nGrowBy`参数会影响内部内存分配，而增长数组。 其使用永远不会影响数组大小由报告[GetSize](#getsize)和[GetUpperBound](#getupperbound)。 如果使用默认值，MFC 中分配内存计算以避免内存碎片并优化对于大部分程序来说效率的方式。  
  
### <a name="example"></a>示例  
  请参阅示例[GetData](#getdata)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例收集](../../visual-cpp-samples.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CObArray 类](../../mfc/reference/cobarray-class.md)   
 [集合类帮助器](../../mfc/reference/collection-class-helpers.md)
