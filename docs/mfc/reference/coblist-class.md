---
title: "CObList 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], lists of
- CObList class
- lists, object
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
caps.latest.revision: 20
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
ms.openlocfilehash: dc95f76be56f00f4779724facaf668a72b3d5ed6
ms.lasthandoff: 02/24/2017

---
# <a name="coblist-class"></a>CObList 类
有序列表的非唯一的 fSupports`CObject`指针访问按顺序或指针值。  
  
## <a name="syntax"></a>语法  
  
```  
class CObList : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CObList::CObList](#coblist)|构造一个空列表`CObject`指针。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CObList::AddHead](#addhead)|将一个元素 （或另一个列表中的所有元素） 添加到 （会生成新的头） 的列表的开头。|  
|[CObList::AddTail](#addtail)|将一个元素 （或另一个列表中的所有元素） 添加到 （会生成新的结尾） 列表的末尾。|  
|[CObList::Find](#find)|获取指针值所指定的元素的位置。|  
|[CObList::FindIndex](#findindex)|获取指定的元素的从零开始的索引位置。|  
|[CObList::GetAt](#getat)|获取位于给定位置的元素。|  
|[CObList::GetCount](#getcount)|返回此列表中的元素数。|  
|[CObList::GetHead](#gethead)|返回的列表 （不能为空） 的头元素。|  
|[CObList::GetHeadPosition](#getheadposition)|返回列表的头元素的位置。|  
|[CObList::GetNext](#getnext)|获取用于循环的下一个元素。|  
|[CObList::GetPrev](#getprev)|获取循环访问的上一个元素。|  
|[CObList::GetSize](#getsize)|返回此列表中的元素数。|  
|[CObList::GetTail](#gettail)|返回 （不能为空） 的列表的结尾元素。|  
|[CObList::GetTailPosition](#gettailposition)|返回列表的结尾元素的位置。|  
|[CObList::InsertAfter](#insertafter)|在给定位置后插入一个新元素。|  
|[CObList::InsertBefore](#insertbefore)|将插入一个新的给定位置之前的元素。|  
|[CObList::IsEmpty](#isempty)|空列表条件 （元素） 的的测试。|  
|[CObList::RemoveAll](#removeall)|从此列表中移除所有元素。|  
|[CObList::RemoveAt](#removeat)|从此列表中，指定位置移除的元素。|  
|[CObList::RemoveHead](#removehead)|从列表头中移除的元素。|  
|[CObList::RemoveTail](#removetail)|从列表的结尾移除的元素。|  
|[CObList::SetAt](#setat)|设置给定位置的元素。|  
  
## <a name="remarks"></a>备注  
 `CObList`列表类似于双向链接列表。  
  
 类型的变量**位置**至关重要的列表。 您可以使用**位置**变量作为迭代器来按顺序遍历列表和一个书签以保存一个位置。 位置并不相同索引，但是。  
  
 插入元素非常快速位于列表的头、 尾和已知**位置**。 顺序搜索则需要按值或索引查找元素。 此搜索速度较慢，如果列表太长。  
  
 `CObList` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。 如果一份`CObject`指针存储到存档中，使用重载的插入运算符或`Serialize`成员函数，每个`CObject`反过来序列化元素。  
  
 如果您需要单独的转储`CObject`列表中的元素，必须将转储上下文的深度设置为 1 或更高版本。  
  
 当`CObList`对象被删除，或删除其元素是时，仅`CObject`指针将被删除，它们不是对象引用。  
  
 可以派生您自己的类从`CObList`。 新的列表类，专门用于存储到派生自的对象的指针`CObject`，添加新的数据成员和新成员函数。 注意，生成的列表并不严格类型安全的因为它允许任何插入`CObject`指针。  
  
> [!NOTE]
>  必须使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)您如果想要将列表序列化的派生类的实现中的宏。  
  
 有关详细信息使用`CObList`，请参阅文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObList`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcoll.h  
  
##  <a name="addhead"></a>CObList::AddHead  
 将新元素的列表添加到此列表的开头。  
  
```  
POSITION AddHead(CObject* newElement);  
void AddHead(CObList* pNewList);
```  
  
### <a name="parameters"></a>参数  
 `newElement`  
 `CObject`指针以添加到此列表。  
  
 `pNewList`  
 一个指向另一个`CObList`列表。 中的元素`pNewList`将添加到此列表。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回**位置**新插入的元素的值。  
  
 下表显示了其他成员函数类似于`CObList::AddHead`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 AddHead (void\* ** `newElement` **);**<br /><br /> **void AddHead (CPtrList\* ** `pNewList` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 AddHead (const CString &** `newElement` **);**<br /><br /> **位置 AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList\* ** `pNewList` **);**|  
  
### <a name="remarks"></a>备注  
 列表可以为空操作之前。  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&89;](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]  
  
 此程序的结果如下所示︰  
  
 `AddHead example: A CObList with 2 elements`  
  
 `a CAge at $44A8 40`  
  
 `a CAge at $442A 21`  
  
##  <a name="addtail"></a>CObList::AddTail  
 将新元素的列表添加到此列表的末尾。  
  
```  
POSITION AddTail(CObject* newElement);  
void AddTail(CObList* pNewList);
```  
  
### <a name="parameters"></a>参数  
 `newElement`  
 `CObject`指针以添加到此列表。  
  
 `pNewList`  
 一个指向另一个`CObList`列表。 中的元素`pNewList`将添加到此列表。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回**位置**新插入的元素的值。  
  
### <a name="remarks"></a>备注  
 列表可以为空操作之前。  
  
 下表显示了其他成员函数类似于`CObList::AddTail`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 AddTail (void\* ** `newElement` **);**<br /><br /> **void AddTail (CPtrList\* ** `pNewList` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 AddTail (const CString &** `newElement` **);**<br /><br /> **位置 AddTail (LPCTSTR** `newElement` **);**<br /><br /> **void AddTail (CStringList\* ** `pNewList` **);**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&90;](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]  
  
 此程序的结果如下所示︰  
  
 `AddTail example: A CObList with 2 elements`  
  
 `a CAge at $444A 21`  
  
 `a CAge at $4526 40`  
  
##  <a name="coblist"></a>CObList::CObList  
 构造一个空`CObject`指针列表。  
  
```  
CObList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>参数  
 `nBlockSize`  
 扩展列表的内存分配粒度。  
  
### <a name="remarks"></a>备注  
 当列表的增长，单位为分配内存`nBlockSize`条目。 如果内存分配失败，`CMemoryException`引发。  
  
 下表显示了其他成员函数类似于`CObList::CObList`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|  
  
### <a name="example"></a>示例  
  下面列出了的`CObject`的派生类`CAge`集合的所有示例中使用︰  
  
 [!code-cpp[NVC_MFCCollections #&91;](../../mfc/codesnippet/cpp/coblist-class_3.h)]  
  
 下面是一个示例的`CObList`构造函数使用情况︰  
  
 [!code-cpp[NVC_MFCCollections #&92;](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]  
  
##  <a name="find"></a>CObList::Find  
 按顺序来查找第一个在列表中搜索`CObject`匹配的指定指针`CObject`指针。  
  
```  
POSITION Find(
    CObject* searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 `searchValue`  
 要在此列表中找到的对象指针。  
  
 `startAfter`  
 搜索起始位置。  
  
### <a name="return-value"></a>返回值  
 一个**位置**可以用于迭代或检索对象指针; 值**NULL**如果未找到的对象。  
  
### <a name="remarks"></a>备注  
 请注意将指针值进行比较，而非对象的内容。  
  
 下表显示了其他成员函数类似于`CObList::Find`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置查找 (void\* ** `searchValue` **，位置** `startAfter` **= NULL) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置查找 (LPCTSTR** `searchValue` **，位置** `startAfter` **= NULL) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&93;](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]  
  
##  <a name="findindex"></a>CObList::FindIndex  
 使用值为`nIndex`作为列表的索引。  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要找的列表中元素的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 一个**位置**可以用于迭代或检索对象指针; 值**NULL**如果`nIndex`太大。 (该框架将生成断言，如果`nIndex`为负。)  
  
### <a name="remarks"></a>备注  
 它从列表中，停止上的开头开始按顺序进行扫描*n*th 元素。  
  
 下表显示了其他成员函数类似于`CObList::FindIndex`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 FindIndex (INT_PTR** `nIndex` **) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 FindIndex (INT_PTR** `nIndex` **) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&94;](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]  
  
##  <a name="getat"></a>CObList::GetAt  
 类型的变量**位置**至关重要的列表。  
  
```  
CObject*& GetAt(POSITION position);  
const CObject*& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 一个**位置**返回先前值`GetHeadPosition`或**查找**成员函数调用。  
  
### <a name="return-value"></a>返回值  
 请参见的返回值说明[GetHead](#gethead)。  
  
### <a name="remarks"></a>备注  
 它不同时，作为一种索引，并不能对操作**位置**您自己的值。 `GetAt`检索`CObject`与给定位置相关联的指针。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 下表显示了其他成员函数类似于`CObList::GetAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetAt (位置***位置* **) const;**<br /><br /> **void\*& GetAt (位置***位置* **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetAt (位置***位置* **) const;**<br /><br /> **CString & GetAt (位置***位置* **);**|  
  
### <a name="example"></a>示例  
  请参阅示例[FindIndex](#findindex)。  
  
##  <a name="getcount"></a>CObList::GetCount  
 获取此列表中的元素数。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个包含元素计数的整数值。  
  
 下表显示了其他成员函数类似于`CObList::GetCount`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount （) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&95;](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]  
  
##  <a name="gethead"></a>CObList::GetHead  
 获取`CObject`表示此列表的头元素的指针。  
  
```  
CObject*& GetHead();  
const CObject*& GetHead() const;  
```  
  
### <a name="return-value"></a>返回值  
 仅当通过指针访问列表**const CObList**，然后`GetHead`返回`CObject`指针。 这允许要使用仅在赋值语句的右侧的函数，并因此防止进行修改，保护列表。  
  
 如果直接或通过指针向访问列表`CObList`，然后`GetHead`返回对`CObject`指针。 这允许在赋值语句的每一端上使用的函数，因此允许列表条目，以进行修改。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`GetHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
 下表显示了其他成员函数类似于`CObList::GetHead`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetHead （） const; void\*& GetHead （）;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**常量; const CString & GetHead （)CString & GetHead （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 下面的示例演示如何使用`GetHead`赋值语句左侧。  
  
 [!code-cpp[NVC_MFCCollections #&96;](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]  
  
##  <a name="getheadposition"></a>CObList::GetHeadPosition  
 获取此列表的头元素的位置。  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**值，可用于迭代或检索对象指针;**NULL**如果列表为空。  
  
 下表显示了其他成员函数类似于`CObList::GetHeadPosition`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 GetHeadPosition （) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 GetHeadPosition （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&97;](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]  
  
##  <a name="getnext"></a>CObList::GetNext  
 获取标识的列表元素`rPosition`，然后设置`rPosition`到`POSITION`列表中的下一个条目的值。  
  
```  
CObject*& GetNext(POSITION& rPosition);  
const CObject* GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 `rPosition`  
 对引用`POSITION`返回先前值`GetNext`， `GetHeadPosition`，或其他成员函数调用。  
  
### <a name="return-value"></a>返回值  
 请参见的返回值说明[GetHead](#gethead)。  
  
### <a name="remarks"></a>备注  
 您可以使用`GetNext`在向前迭代循环中，如果您建立的初始位置，通过调用`GetHeadPosition`或`Find`。  
  
 您必须确保您`POSITION`值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 如果检索的元素则在列表中，最后的新值`rPosition`设置为`NULL`。  
  
 可执行迭代的过程中删除元素。 请参阅示例[RemoveAt](#removeat)。  
  
> [!NOTE]
>  从 MFC 8.0 开始的 const 版本的此方法已更改返回`const CObject*`而不是`const CObject*&`。  此更改是为了以使编译器符合 c + + 标准。  
  
 下表显示了其他成员函数类似于`CObList::GetNext`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&98;](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]  
  
 此程序的结果如下所示︰  
  
 `a CAge at $479C 40`  
  
 `a CAge at $46C0 21`  
  
##  <a name="getprev"></a>CObList::GetPrev  
 获取标识的列表元素`rPosition`，然后设置`rPosition`到`POSITION`以前在列表中项的值。  
  
```  
CObject*& GetPrev(POSITION& rPosition);  
const CObject* GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 `rPosition`  
 对引用`POSITION`返回先前值`GetPrev`或其他成员函数调用。  
  
### <a name="return-value"></a>返回值  
 请参见的返回值说明[GetHead](#gethead)。  
  
### <a name="remarks"></a>备注  
 您可以使用`GetPrev`在反向迭代循环中，如果您建立的初始位置，通过调用`GetTailPosition`或`Find`。  
  
 您必须确保您`POSITION`值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 如果检索的元素则在列表中，第一个的新值`rPosition`设置为`NULL`。  
  
> [!NOTE]
>  从 MFC 8.0 开始的 const 版本的此方法已更改返回`const CObject*`而不是`const CObject*&`。  此更改是为了以使编译器符合 c + + 标准。  
  
 下表显示了其他成员函数类似于`CObList::GetPrev`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&99;](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]  
  
 此程序的结果如下所示︰  
  
 `a CAge at $421C 21`  
  
 `a CAge at $421C 40`  
  
##  <a name="getsize"></a>CObList::GetSize  
 返回列表中元素的数目。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表中的项数。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索列表中的元素数。  
  
 下表显示了其他成员函数类似于`CObList::GetSize`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize （) 常量;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize （) 常量;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&100;](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]  
  
##  <a name="gettail"></a>CObList::GetTail  
 获取`CObject`表示此列表的结尾元素的指针。  
  
```  
CObject*& GetTail();  
const CObject*& GetTail() const;  
```  
  
### <a name="return-value"></a>返回值  
 请参见的返回值说明[GetHead](#gethead)。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`GetTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
 下表显示了其他成员函数类似于`CObList::GetTail`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetTail （） 常量; void\*& GetTail （）;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const; const CString & GetTail （)CString & GetTail （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&101;](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]  
  
##  <a name="gettailposition"></a>CObList::GetTailPosition  
 获取此列表; 结尾元素的位置**NULL**如果列表为空。  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**值，可用于迭代或检索对象指针;**NULL**如果列表为空。  
  
 下表显示了其他成员函数类似于`CObList::GetTailPosition`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 GetTailPosition （) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 GetTailPosition （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&102;](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]  
  
##  <a name="insertafter"></a>CObList::InsertAfter  
 在指定位置处的元素后，请向此列表中添加一个元素。  
  
```  
POSITION InsertAfter(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 一个由先前 **、** 或 `GetNext`Find `GetPrev`成员函数调用返回的 **位置** 值。  
  
 `newElement`  
 要添加到此列表的对象指针。  
  
 下表显示了其他成员函数类似于`CObList::InsertAfter`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 InsertAfter (位置***位置* **、 void\* ** `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 InsertAfter (位置***位置* **，const CString &** `newElement` **);**<br /><br /> **位置 InsertAfter (位置***位置* **，LPCTSTR** `newElement` **);**|  
  
### <a name="return-value"></a>返回值  
 一个**位置**是相同的值作为*位置*参数。  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&103;](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]  
  
 此程序的结果如下所示︰  
  
 `InsertAfter example: A CObList with 3 elements`  
  
 `a CAge at $4A44 40`  
  
 `a CAge at $4A64 65`  
  
 `a CAge at $4968 21`  
  
##  <a name="insertbefore"></a>CObList::InsertBefore  
 将元素添加到此列表中指定位置处的元素之前。  
  
```  
POSITION InsertBefore(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 一个由先前 **、** 或 `GetNext`Find `GetPrev`成员函数调用返回的 **位置** 值。  
  
 `newElement`  
 要添加到此列表的对象指针。  
  
### <a name="return-value"></a>返回值  
 一个**位置**值，可用于迭代或检索对象指针;**NULL**如果列表为空。  
  
 下表显示了其他成员函数类似于`CObList::InsertBefore`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 InsertBefore (位置***位置* **、 void\* ** `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 InsertBefore (位置***位置* **，const CString &** `newElement` **);**<br /><br /> **位置 InsertBefore (位置***位置* **，LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&104;](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]  
  
 此程序的结果如下所示︰  
  
 `InsertBefore example: A CObList with 3 elements`  
  
 `a CAge at $4AE2 40`  
  
 `a CAge at $4B02 65`  
  
 `a CAge at $49E6 21`  
  
##  <a name="isempty"></a>CObList::IsEmpty  
 指示此列表是否包含任何元素。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果此列表为空，则为非零值否则为 0。  
  
 下表显示了其他成员函数类似于`CObList::IsEmpty`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty （) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty （) const;**|  
  
### <a name="example"></a>示例  
  请参阅示例[RemoveAll](#removeall)。  
  
##  <a name="removeall"></a>CObList::RemoveAll  
 从此列表中移除所有元素，并释放关联`CObList`内存。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 如果列表已为空，则会不生成任何错误。  
  
 当您从中移除元素`CObList`，从列表中删除的对象指针。 它是您要删除这些对象本身的责任。  
  
 下表显示了其他成员函数类似于`CObList::RemoveAll`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll （);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&105;](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]  
  
##  <a name="removeat"></a>CObList::RemoveAt  
 从此列表中移除指定的元素。  
  
```  
void RemoveAt(POSITION position);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 要从列表中移除的元素的位置。  
  
### <a name="remarks"></a>备注  
 当删除从元素`CObList`，从列表中删除的对象指针。 它是您要删除这些对象本身的责任。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 下表显示了其他成员函数类似于`CObList::RemoveAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (位置***位置* **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (位置***位置* **);**|  
  
### <a name="example"></a>示例  
  在列表中迭代期间删除的元素时要小心。 下面的示例演示一种删除方法，可保证有效**位置**值[GetNext](#getnext)。  
  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&106;](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]  
  
 此程序的结果如下所示︰  
  
 `RemoveAt example: A CObList with 2 elements`  
  
 `a CAge at $4C1E 65`  
  
 `a CAge at $4B22 21`  
  
##  <a name="removehead"></a>CObList::RemoveHead  
 从列表头中移除的元素并将指针返回到它。  
  
```  
CObject* RemoveHead();
```  
  
### <a name="return-value"></a>返回值  
 `CObject`以前列表的开头的指针。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`RemoveHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
 下表显示了其他成员函数类似于`CObList::RemoveHead`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead （);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&107; 页](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]  
  
##  <a name="removetail"></a>CObList::RemoveTail  
 从列表的结尾移除的元素并将指针返回到它。  
  
```  
CObject* RemoveTail();
```  
  
### <a name="return-value"></a>返回值  
 指向已在列表末尾的对象的指针。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`RemoveTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
 下表显示了其他成员函数类似于`CObList::RemoveTail`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail （);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&108;](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]  
  
##  <a name="setat"></a>CObList::SetAt  
 设置给定位置的元素。  
  
```  
void SetAt(
    POSITION pos,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 **位置**要设置的元素。  
  
 `newElement`  
 `CObject`写入到列表的指针。  
  
### <a name="remarks"></a>备注  
 类型的变量**位置**至关重要的列表。 它不同时，作为一种索引，并不能对操作**位置**您自己的值。 `SetAt`写入`CObject`到列表中的指定位置的指针。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 下表显示了其他成员函数类似于`CObList::SetAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (位置** `pos` **，const CString &** `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt( POSITION** `pos` **, LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)可以列出`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections #&109;](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]  
  
 此程序的结果如下所示︰  
  
 `SetAt example: A CObList with 2 elements`  
  
 `a CAge at $4D98 40`  
  
 `a CAge at $4DB8 65`  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CStringList 类](../../mfc/reference/cstringlist-class.md)   
 [CPtrList 类](../../mfc/reference/cptrlist-class.md)

