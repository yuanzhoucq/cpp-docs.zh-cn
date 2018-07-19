---
title: CObArray 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1c29a317ff2d4d8e40d6aca0d6b46ee3ba2fd88
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853831"
---
# <a name="cobarray-class"></a>CObArray 类
支持 `CObject` 指针数组。  
  
## <a name="syntax"></a>语法  
  
```  
class CObArray : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CObArray::CObArray](#cobarray)|构造一个空数组`CObject`指针。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CObArray::Add](#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|  
|[CObArray::Append](#append)|将另一个数组追加到该数组中；根据需要扩展该数组。|  
|[CObArray::Copy](#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|  
|[CObArray::ElementAt](#elementat)|在该数组中返回对元素指针的临时引用。|  
|[CObArray::FreeExtra](#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|  
|[CObArray::GetAt](#getat)|返回给定索引位置处的值。|  
|[CObArray::GetCount](#getcount)|获取此数组中的元素数。|  
|[CObArray::GetData](#getdata)|允许访问该数组中的元素。 可以为 NULL。|  
|[CObArray::GetSize](#getsize)|获取此数组中的元素数。|  
|[CObArray::GetUpperBound](#getupperbound)|返回最大的有效索引。|  
|[CObArray::InsertAt](#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|  
|[CObArray::IsEmpty](#isempty)|确定数组是否为空。|  
|[CObArray::RemoveAll](#removeall)|从此数组中移除所有元素。|  
|[CObArray::RemoveAt](#removeat)|移除特定索引处的元素。|  
|[CObArray::SetAt](#setat)|设置给定索引的值；不允许对该数组进行扩展。|  
|[CObArray::SetAtGrow](#setatgrow)|设置给定索引的值；根据需要扩展该数组。|  
|[CObArray::SetSize](#setsize)|设置要在该数组中包含的元素数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CObArray::operator]](#operator_at)|设置或获取位于指定索引处的元素。|  
  
## <a name="remarks"></a>备注  
 这些对象数组是类似于 C 数组，但它们可以动态缩小和增大。  
  
 数组索引始终在位置 0 处开始。 您可以决定是修复上限还是允许要展开时添加过去的当前绑定元素的数组。 内存是连续分配给了上限，即使某些元素是 null。  
  
 在 Win32 下的大小`CObArray`对象是仅限于可用内存。  
  
 与使用 C 数组，访问时间`CObArray`索引的元素是常量，它独立于数组大小。  
  
 `CObArray` 集成了 IMPLEMENT_SERIAL 宏来支持序列化和转储的它的元素。 如果数组`CObject`指针存储到存档，或者用重载的插入运算符`Serialize`成员函数，每个`CObject`元素，反过来，序列化以及其数组的索引。  
  
 如果你需要个人的转储`CObject`数组中的元素，则必须设置的深度`CDumpContext`等于或大于 1 的对象。  
  
 当`CObArray`删除对象，或删除其元素是时，仅`CObject`指针将被删除，它们引用而非的对象。  
  
> [!NOTE]
>  在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。  
  
 数组类派生是类似于列表派生。 有关特殊用途的列表类派生的详细信息，请参阅文章[集合](../../mfc/collections.md)。  
  
> [!NOTE]
>  如果所要序列化数组，则必须在派生类的实现中使用 IMPLEMENT_SERIAL 宏。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObArray`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcoll.h  
  
##  <a name="add"></a>  CObArray::Add  
 将新元素添加到数组，按 1 增长数组的末尾。  
  
```  
INT_PTR Add(CObject* newElement);
```  
  
### <a name="parameters"></a>参数  
 *newElement*  
 `CObject`用于添加到该数组的指针。  
  
### <a name="return-value"></a>返回值  
 添加的元素的索引。  
  
### <a name="remarks"></a>备注  
 如果[SetSize](#setsize)已用于*nGrowBy*可能分配值大于 1，则额外的内存。 但是，仅为 1 将提高上限。  
  
 下表显示其他成员函数类似于`CObArray::Add`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR 添加 (字节** `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR 添加 (DWORD** `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR 添加 (void\***  `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR 添加 (LPCTSTR** `newElement` **); 引发 (CMemoryException\* );**<br /><br /> **INT_PTR Add(const CString&** `newElement` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR 添加 (UINT** `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR 添加 (WORD** `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]  
  
 此程序的结果如下所示：  
  
 `Add example: A CObArray with 2 elements`  
  
 `[0] = a CAge at $442A 21`  
  
 `[1] = a CAge at $4468 40`  
  
##  <a name="append"></a>  CObArray::Append  
 调用此成员函数以将另一个数组的内容添加到给定数组的末尾。  
  
```  
INT_PTR Append(const CObArray& src);
```  
  
### <a name="parameters"></a>参数  
 *src*  
 要追加到该数组的元素的源。  
  
### <a name="return-value"></a>返回值  
 第一个追加的元素的索引。  
  
### <a name="remarks"></a>备注  
 数组必须是类型的相同。  
  
 如有必要，`Append`可能会分配额外内存来容纳追加到该数组的元素。  
  
 下表显示其他成员函数类似于`CObArray::Append`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR 追加 (const CByteArray &** *src* **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR 追加 (const CDWordArray &** *src* **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR 追加 (const CPtrArray &** *src* **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR 追加 (const CStringArray &** *src* **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR 追加 (const CUIntArray &** *src* **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR 追加 (const CWordArray &** *src* **);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]  
  
##  <a name="copy"></a>  CObArray::Copy  
 调用此成员函数以使用相同类型的另一个数组的元素覆盖给定数组的元素。  
  
```  
void Copy(const CObArray& src);
```  
  
### <a name="parameters"></a>参数  
 *src*  
 要复制到数组的元素的源。  
  
### <a name="remarks"></a>备注  
 `Copy` 不会释放内存;但是，如果有必要，`Copy`可能会分配额外内存来容纳复制到数组的元素。  
  
 下表显示其他成员函数类似于`CObArray::Copy`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void 副本 (const CByteArray &** *src* **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void 副本 (const CDWordArray &** *src* **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void 副本 (const CPtrArray &** *src* **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void 副本 (const CStringArray &** *src* **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void 副本 (const CUIntArray &** *src* **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void 副本 (const CWordArray &** *src* **);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]  
  
##  <a name="cobarray"></a>  CObArray::CObArray  
 构造一个空`CObject`指针数组。  
  
```  
CObArray();
```  
  
### <a name="remarks"></a>备注  
 数组每次增加一个元素。  
  
 下表显示了类似于其他构造函数`CObArray::CObArray`。  
  
|类|构造函数|  
|-----------|-----------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray （);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray （);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray （);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray （);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray （);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray （);**|  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]  
  
##  <a name="elementat"></a>  CObArray::ElementAt  
 在该数组中返回对元素指针的临时引用。  
  
```  
CObject*& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 大于或等于 0 的整数索引且小于或等于返回的值`GetUpperBound`。  
  
### <a name="return-value"></a>返回值  
 对引用`CObject`指针。  
  
### <a name="remarks"></a>备注  
 它用于实现数组的左侧赋值运算符。 请注意，这是应仅用于实现特殊数组运算符的高级的函数。  
  
 下表显示其他成员函数类似于`CObArray::ElementAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**字节和 ElementAt (INT_PTR** `nIndex` **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & ElementAt (INT_PTR** `nIndex` **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& ElementAt (INT_PTR** `nIndex` **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString & ElementAt (INT_PTR** `nIndex` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & ElementAt (INT_PTR** `nIndex` **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD 和 ElementAt (INT_PTR** `nIndex` **);**|  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CObArray::GetSize](#getsize)。  
  
##  <a name="freeextra"></a>  CObArray::FreeExtra  
 释放任何已分配，而数组已增长的额外内存。  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>备注  
 此函数无效的大小或数组的上限。  
  
 下表显示其他成员函数类似于`CObArray::FreeExtra`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra （);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra （);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra （);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra （);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra （);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra （);**|  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CObArray::GetData](#getdata)。  
  
##  <a name="getat"></a>  CObArray::GetAt  
 返回指定索引处的数组元素。  
  
```  
CObject* GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 大于或等于 0 的整数索引且小于或等于返回的值`GetUpperBound`。  
  
### <a name="return-value"></a>返回值  
 `CObject`指针当前位于此索引处的元素。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  传递值为负或值大于返回的值`GetUpperBound`将导致失败的断言。  
  
 下表显示其他成员函数类似于`CObArray::GetAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**字节 GetAt (INT_PTR** `nIndex` **) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt (INT_PTR** `nIndex` **) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt (INT_PTR** `nIndex` **) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt (INT_PTR** `nIndex` **) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt (INT_PTR** `nIndex` **) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt (INT_PTR** `nIndex` **) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]  
  
##  <a name="getcount"></a>  CObArray::GetCount  
 返回数组元素的个数。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 数组中的项数。  
  
### <a name="remarks"></a>备注  
 调用此方法来检索数组中的元素数。 因为索引是从零开始，大小为 1 大于最大的索引。  
  
 下表显示其他成员函数类似于`CObArray::GetCount`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount （) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount （) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount （) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount （) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount （) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]  
  
##  <a name="getdata"></a>  CObArray::GetData  
 使用此成员函数来直接访问数组中的元素。  
  
```  
const CObject** GetData() const;  
  
CObject** GetData();
```  
  
### <a name="return-value"></a>返回值  
 指向数组的指针`CObject`指针。  
  
### <a name="remarks"></a>备注  
 如果没有元素可用，`GetData`返回 null 值。  
  
 对数组的元素的直接访问可帮助你更快地工作，而时要格外小心调用`GetData`; 直接进行的任何错误会影响在数组的元素。  
  
 下表显示其他成员函数类似于`CObArray::GetData`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**const 字节\*const; GetData （)字节\*GetData （);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**const DWORD\* GetData （） const; DWORD\* GetData （);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**const void\* \* GetData （) const; void\* \* GetData （);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\* const; GetData （)CString\* GetData （);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**const UINT\* const; GetData （)UINT\* GetData （);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**const WORD\* const; GetData （)WORD\* GetData （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]  
  
##  <a name="getsize"></a>  CObArray::GetSize  
 返回数组的大小。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>备注  
 由于索引是从零开始的则大小将为 1 大于最大的索引。  
  
 下表显示其他成员函数类似于`CObArray::GetSize`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize （) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize （) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize （) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize （) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize （) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]  
  
##  <a name="getupperbound"></a>  CObArray::GetUpperBound  
 返回此数组的当前的上限。  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="return-value"></a>返回值  
 （从零开始） 的上限的索引。  
  
### <a name="remarks"></a>备注  
 数组索引是从零开始的因为此函数返回值 1 小于`GetSize`。  
  
 条件`GetUpperBound( )`=-1 指示该数组包含任何元素。  
  
 下表显示其他成员函数类似于`CObArray::GetUpperBound`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound （) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound （) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound （) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound （) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound （) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]  
  
##  <a name="insertat"></a>  CObArray::InsertAt  
 在指定索引处插入一个元素（或另一个数组中的所有元素）。  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    CObject* newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CObArray* pNewArray);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 可能会高于返回的值的整数索引`GetUpperBound`。  
  
 *newElement*  
 `CObject`用于放置在此数组的指针。 一个*newElement*值的允许为 NULL。  
  
 *nCount*  
 此元素应为次数插入 （默认值为 1）。  
  
 *nStartIndex*  
 可能会高于返回的值的整数索引`GetUpperBound`。  
  
 *pNewArray*  
 另一个数组，其中包含要添加到该数组的元素。  
  
### <a name="remarks"></a>备注  
 第一个版本`InsertAt`数组中指定索引处插入一个元素 （或一个元素的多个副本）。 在过程中，它上移 （通过递增索引） 在此索引和它的现有元素上移其上的所有元素。  
  
 第二个版本将所有元素都插入从另一`CObArray`集合，开始*nStartIndex*位置。  
  
 `SetAt`函数，与此相反，替换一个指定的数组元素，并不移动任何元素。  
  
 下表显示其他成员函数类似于`CObArray::InsertAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，字节** `newElement` **，int** `nCount` **= 1);**<br /><br /> **引发 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CByteArray\***  `pNewArray` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，DWORD** `newElement` **，int** `nCount` **= 1);**<br /><br /> **引发 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CDWordArray\***  `pNewArray` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，void\***  `newElement` **，int** `nCount` **= 1);**<br /><br /> **引发 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CPtrArray\***  `pNewArray` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，LPCTSTR** `newElement` **，int** `nCount` **= 1);**<br /><br /> **引发 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CStringArray\***  `pNewArray` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，UINT** `newElement` **，int** `nCount` **= 1);**<br /><br /> **引发 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CUIntArray\***  `pNewArray` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，WORD** `newElement` **，int** `nCount` **= 1);**<br /><br /> **引发 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CWordArray\***  `pNewArray` **);**<br /><br /> **引发 (CMemoryException\* );**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]  
  
 此程序的结果如下所示：  
  
 `InsertAt example: A CObArray with 3 elements`  
  
 `[0] = a CAge at $45C8 21`  
  
 `[1] = a CAge at $4646 30`  
  
 `[2] = a CAge at $4606 40`  
  
##  <a name="isempty"></a>  CObArray::IsEmpty  
 确定数组是否为空。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果数组为空，则为非零值否则为 0。  
  
##  <a name="operator_at"></a>  CObArray::operator]  
 这些下标运算符不方便代替`SetAt`和`GetAt`函数。  
  
```  
CObject*& operator[](int_ptr nindex);  
CObject* operator[](int_ptr nindex) const;  
```  
  
### <a name="remarks"></a>备注  
 第一个运算符为数组不是调用**const**，可以在赋值语句左侧 （左值） 或右侧 （右值） 一起使用。 第二个，为调用**const**数组，可能会使用仅在右侧。  
  
 在库的调试版本断言的下标 （无论在左侧或右侧的赋值语句） 是否超出界限。  
  
 下表显示了类似于其他运算符`CObArray::operator []`。  
  
|类|运算符|  
|-----------|--------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**字节 & 运算符 [] (int_ptr** `nindex`  **\);**<br /><br /> **BYTE 运算符 [] (int_ptr** `nindex`  **\) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & 运算符 [] (int_ptr** `nindex`  **\);**<br /><br /> **DWORD 运算符 [] (int_ptr** `nindex`  **\) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& 运算符 [] (int_ptr** `nindex`  **\);**<br /><br /> **void\* operator [] (int_ptr** `nindex`  **\) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString & 运算符 [] (int_ptr** `nindex`  **\);**<br /><br /> **CString 运算符 [] (int_ptr** `nindex`  **\) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & 运算符 [] (int_ptr** `nindex`  **\);**<br /><br /> **UINT 运算符 [] (int_ptr** `nindex`  **\) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & 运算符 [] (int_ptr** `nindex`  **\);**<br /><br /> **WORD 运算符 [] (int_ptr** `nindex`  **\) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]  
  
##  <a name="removeall"></a>  CObArray::RemoveAll  
 此数组中移除所有指针，但不实际删除`CObject`对象。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 如果已经为空数组，该函数仍然正常工作。  
  
 `RemoveAll`函数释放指针存储所使用的所有内存。  
  
 下表显示其他成员函数类似于`CObArray::RemoveAll`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll （);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll （);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll （);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll （);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll （);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]  
  
##  <a name="removeat"></a>  CObArray::RemoveAt  
 移除数组中指定索引处开始的一个或多个元素。  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 大于或等于 0 的整数索引且小于或等于返回的值`GetUpperBound`。  
  
 *nCount*  
 要移除的元素数。  
  
### <a name="remarks"></a>备注  
 在过程中，移向上述的已删除的元素的所有元素下。 它递减右上绑定的数组，但不会释放内存。  
  
 如果你尝试删除不是上面的删除点数组中包含的更多元素，然后在库的调试版本断言。  
  
 `RemoveAt`函数删除`CObject`指针数组，但它不会删除该对象本身。  
  
 下表显示其他成员函数类似于`CObArray::RemoveAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** *nCount* **= 1);**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]  
  
 此程序的结果如下所示：  
  
 `RemoveAt example: A CObArray with 1 elements`  
  
 `[0] = a CAge at $4606 40`  
  
##  <a name="setat"></a>  CObArray::SetAt  
 设置指定索引处的数组元素。  
  
```  
void SetAt(
    INT_PTR nIndex,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 大于或等于 0 的整数索引且小于或等于返回的值`GetUpperBound`。  
  
 *newElement*  
 要插入此数组中的对象指针。 允许 NULL 值。  
  
### <a name="remarks"></a>备注  
 `SetAt` 不会导致要增长的数组。 使用`SetAtGrow`如果你想要自动增长的数组。  
  
 您必须确保你的索引值表示数组中的有效位置。 如果该值超出界限，调试版本的库断言。  
  
 下表显示其他成员函数类似于`CObArray::SetAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt (INT_PTR** `nIndex` **，字节** `newElement` **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **，DWORD** `newElement` **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt (INT_PTR** `nIndex` **，void\***  `newElement` **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt (INT_PTR** `nIndex` **，LPCTSTR** `newElement` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt (INT_PTR** `nIndex` **，UINT** `newElement` **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **，WORD** `newElement` **);**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]  
  
 此程序的结果如下所示：  
  
 `SetAt example: A CObArray with 2 elements`  
  
 `[0] = a CAge at $47E0 30`  
  
 `[1] = a CAge at $47A0 40`  
  
##  <a name="setatgrow"></a>  CObArray::SetAtGrow  
 设置指定索引处的数组元素。  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 一个大于或等于 0 的整数索引。  
  
 *newElement*  
 要添加到该数组的对象指针。 允许 NULL 值。  
  
### <a name="remarks"></a>备注  
 如有必要，该数组自动增长 （即，上限为进行调整以容纳新元素）。  
  
 下表显示其他成员函数类似于`CObArray::SetAtGrow`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，字节** `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，DWORD** `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，void\***  `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，LPCTSTR** `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，UINT** `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，WORD** `newElement` **);**<br /><br /> **引发 (CMemoryException\* );**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`集合的所有示例中使用的类。  
  
 [!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]  
  
 此程序的结果如下所示：  
  
 `SetAtGrow example: A CObArray with 4 elements`  
  
 `[0] = a CAge at $47C0 21`  
  
 `[1] = a CAge at $4800 40`  
  
 `[2] = NULL`  
  
 `[3] = a CAge at $4840 65`  
  
##  <a name="setsize"></a>  CObArray::SetSize  
 建立一个空的或现有的数组; 的大小如有必要，请分配内存。  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>参数  
 *nNewSize*  
 新数组大小 （元素的数量）。 必须是大于或等于 0。  
  
 *nGrowBy*  
 元素槽分配的大小增长是否需要最小数目。  
  
### <a name="remarks"></a>备注  
 如果新大小小于旧大小，该数组被截断，并释放所有未使用的内存。 为提高效率，调用`SetSize`使用它之前设置数组的大小。 这可以防止重新分配和每次添加一个项数组复制的需要。  
  
 *NGrowBy*参数会影响内部内存分配，而增长数组。 其用途永远不会影响数组大小由报告`GetSize`和`GetUpperBound`。  
  
 如果数组的大小已增长，所有新分配**CObject \*** 指针设置为 NULL。  
  
 下表显示其他成员函数类似于`CObArray::SetSize`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **引发 (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **引发 (CMemoryException\* );**|  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CObArray::GetData](#getdata)。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CStringArray 类](../../mfc/reference/cstringarray-class.md)   
 [CPtrArray 类](../../mfc/reference/cptrarray-class.md)   
 [CByteArray 类](../../mfc/reference/cbytearray-class.md)   
 [CWordArray 类](../../mfc/reference/cwordarray-class.md)   
 [CDWordArray 类](../../mfc/reference/cdwordarray-class.md)
