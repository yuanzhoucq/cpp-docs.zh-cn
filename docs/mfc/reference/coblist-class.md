---
title: CObList 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf937f11118cfbea26db11ba48ea0ed65d903af6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217150"
---
# <a name="coblist-class"></a>CObList 类
有序列表的唯一，则 fSupports`CObject`指针可访问按顺序或指针值。  
  
## <a name="syntax"></a>语法  
  
```  
class CObList : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CObList::CObList](#coblist)|构造一个空列表`CObject`指针。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CObList::AddHead](#addhead)|将一个元素 （或另一个列表中的所有元素） 添加到 （使新头） 了列表的开头。|  
|[CObList::AddTail](#addtail)|将一个元素 （或另一个列表中的所有元素） 添加到列表 （使新结尾） 的尾部。|  
|[CObList::Find](#find)|获取指针值所指定的元素的位置。|  
|[CObList::FindIndex](#findindex)|获取指定的从零开始的索引的元素的位置。|  
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
|[CObList::InsertBefore](#insertbefore)|将插入新元素之前的给定位置。|  
|[CObList::IsEmpty](#isempty)|对于空列表条件 （元素） 的测试。|  
|[CObList::RemoveAll](#removeall)|此列表中移除所有元素。|  
|[CObList::RemoveAt](#removeat)|从此列表中，指定位置移除一个元素。|  
|[CObList::RemoveHead](#removehead)|从列表的开头移除的元素。|  
|[CObList::RemoveTail](#removetail)|从列表的结尾移除的元素。|  
|[CObList::SetAt](#setat)|设置给定位置处的元素。|  
  
## <a name="remarks"></a>备注  
 `CObList` 列表类似于双向链接列表。  
  
 位置类型的变量是列表的键。 作为要按顺序遍历列表的迭代器和一个书签，用于保存一个位置，可以使用位置变量。 位置不是相同的索引，但是。  
  
 元素插入速度非常快列表头、 尾和已知位置。 按值或索引查找元素所需顺序搜索。 此搜索可能较慢，如果列表太长。  
  
 `CObList` 集成了 IMPLEMENT_SERIAL 宏来支持序列化和转储的它的元素。 如果一系列`CObject`指针存储到存档，或者用重载的插入运算符`Serialize`成员函数，每个`CObject`反过来序列化元素。  
  
 如果你需要个人的转储`CObject`列表中的元素，必须将转储上下文的深度设置为 1 或更高版本。  
  
 当`CObList`删除对象，或删除其元素是时，仅`CObject`指针将被删除，它们引用而非的对象。  
  
 可以派生您自己的类从`CObList`。 新列表类，设计用来存放指针到派生自`CObject`，添加了新的数据成员和新的成员函数。 请注意，所得到的列表并不严格类型安全的因为它允许任何插入`CObject`指针。  
  
> [!NOTE]
>  必须使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)如果你想要序列化列表为派生类的实现中的宏。  
  
 有关使用的详细信息`CObList`，请参阅文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObList`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcoll.h  
  
##  <a name="addhead"></a>  CObList::AddHead  
 将新元素的列表添加到此列表的开头。  
  
```  
POSITION AddHead(CObject* newElement);  
void AddHead(CObList* pNewList);
```  
  
### <a name="parameters"></a>参数  
 *newElement*  
 `CObject`用于添加到此列表的指针。  
  
 *pNewList*  
 指向另一个`CObList`列表。 中的元素*pNewList*将添加到此列表。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回新插入的元素的位置值。  
  
 下表显示其他成员函数类似于`CObList::AddHead`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 AddHead (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead (CPtrList** <strong>\*</strong> `pNewList` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 AddHead (const CString &** `newElement` **);**<br /><br /> **位置 AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList** <strong>\*</strong> `pNewList` **);**|  
  
### <a name="remarks"></a>备注  
 列表可以为空操作之前。  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]  
  
 此程序的结果如下所示：  
  
 `AddHead example: A CObList with 2 elements`  
  
 `a CAge at $44A8 40`  
  
 `a CAge at $442A 21`  
  
##  <a name="addtail"></a>  CObList::AddTail  
 将新元素的列表添加到此列表的结尾。  
  
```  
POSITION AddTail(CObject* newElement);  
void AddTail(CObList* pNewList);
```  
  
### <a name="parameters"></a>参数  
 *newElement*  
 `CObject`用于添加到此列表的指针。  
  
 *pNewList*  
 指向另一个`CObList`列表。 中的元素*pNewList*将添加到此列表。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回新插入的元素的位置值。  
  
### <a name="remarks"></a>备注  
 列表可以为空操作之前。  
  
 下表显示其他成员函数类似于`CObList::AddTail`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 AddTail (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail (CPtrList** <strong>\*</strong> `pNewList` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 AddTail (const CString &** `newElement` **);**<br /><br /> **位置 AddTail (LPCTSTR** `newElement` **);**<br /><br /> **void AddTail (CStringList** <strong>\*</strong> `pNewList` **);**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]  
  
 此程序的结果如下所示：  
  
 `AddTail example: A CObList with 2 elements`  
  
 `a CAge at $444A 21`  
  
 `a CAge at $4526 40`  
  
##  <a name="coblist"></a>  CObList::CObList  
 构造一个空`CObject`指针列表。  
  
```  
CObList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>参数  
 *nBlockSize*  
 扩展列表的内存分配粒度。  
  
### <a name="remarks"></a>备注  
 随着在列表中的单元分配内存*nBlockSize*条目。 如果内存分配失败，`CMemoryException`引发。  
  
 下表显示其他成员函数类似于`CObList::CObList`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|  
  
### <a name="example"></a>示例  
  下面是一系列`CObject`的派生类`CAge`集合的所有示例中使用：  
  
 [!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]  
  
 下面是一个示例的`CObList`构造函数使用情况：  
  
 [!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]  
  
##  <a name="find"></a>  CObList::Find  
 按顺序以找到第一个在列表中搜索`CObject`匹配的指定指针`CObject`指针。  
  
```  
POSITION Find(
    CObject* searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 *searchValue*  
 要在此列表中找到的对象指针。  
  
 *startAfter*  
 搜索起始位置。  
  
### <a name="return-value"></a>返回值  
 可用于迭代或检索对象指针; 一个位置值如果未找到该对象为 NULL。  
  
### <a name="remarks"></a>备注  
 请注意，指针值进行比较，而非对象的内容。  
  
 下表显示其他成员函数类似于`CObList::Find`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置找到 (void** <strong>\*</strong> `searchValue` **，位置** `startAfter` **= NULL) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置查找 (LPCTSTR** `searchValue` **，位置** `startAfter` **= NULL) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]  
  
##  <a name="findindex"></a>  CObList::FindIndex  
 使用的值*nIndex*作为列表中的索引。  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 要找的列表元素的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 可用于迭代或检索对象指针; 一个位置值则为 NULL *nIndex*太大。 (如果，框架才生成断言*nIndex*为负。)  
  
### <a name="remarks"></a>备注  
 从列表中，停止对的开头开始顺序扫描*n*个元素。  
  
 下表显示其他成员函数类似于`CObList::FindIndex`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 FindIndex (INT_PTR** `nIndex` **) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 FindIndex (INT_PTR** `nIndex` **) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]  
  
##  <a name="getat"></a>  CObList::GetAt  
 位置类型的变量是列表的键。  
  
```  
CObject*& GetAt(POSITION position);  
const CObject*& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 返回先前的位置值`GetHeadPosition`或`Find`成员函数调用。  
  
### <a name="return-value"></a>返回值  
 请参阅的返回值描述[GetHead](#gethead)。  
  
### <a name="remarks"></a>备注  
 不是索引，请与相同和您无法对位置值自己。 `GetAt` 检索`CObject`与给定位置相关联的指针。  
  
 您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。  
  
 下表显示其他成员函数类似于`CObList::GetAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetAt (位置***位置* **) const;**<br /><br /> **void\*& GetAt (位置***位置* **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetAt (位置***位置* **) const;**<br /><br /> **CString & GetAt (位置***位置* **);**|  
  
### <a name="example"></a>示例  
  有关示例，请参阅[FindIndex](#findindex)。  
  
##  <a name="getcount"></a>  CObList::GetCount  
 获取此列表中的元素数。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个包含元素计数的整数值。  
  
 下表显示其他成员函数类似于`CObList::GetCount`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount （) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]  
  
##  <a name="gethead"></a>  CObList::GetHead  
 获取`CObject`表示此列表的头元素的指针。  
  
```  
CObject*& GetHead();  
const CObject*& GetHead() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果通过到指针访问列表`const CObList`，然后`GetHead`返回`CObject`指针。 这允许使用仅在赋值语句右侧的函数，因此，从修改保护列表。  
  
 如果直接或通过指针向访问列表`CObList`，然后`GetHead`返回的引用`CObject`指针。 这允许使用赋值语句的任何一侧的函数，因此允许列表条目，以进行修改。  
  
### <a name="remarks"></a>备注  
 必须确保该列表不是空之前调用`GetHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
 下表显示其他成员函数类似于`CObList::GetHead`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetHead （) const; void\*& GetHead （);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetHead （) const;CString & GetHead （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 下面的示例演示如何使用`GetHead`赋值语句左侧。  
  
 [!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]  
  
##  <a name="getheadposition"></a>  CObList::GetHeadPosition  
 获取此列表的头元素的位置。  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 可用于迭代或检索对象指针; 一个位置值如果列表为空，则为 NULL。  
  
 下表显示其他成员函数类似于`CObList::GetHeadPosition`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 GetHeadPosition （) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 GetHeadPosition （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]  
  
##  <a name="getnext"></a>  CObList::GetNext  
 获取标识的列表元素*rPosition*，然后设置*rPosition*到`POSITION`列表中的下一个条目的值。  
  
```  
CObject*& GetNext(POSITION& rPosition);  
const CObject* GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 *rPosition*  
 对先前返回的位置值的引用`GetNext`， `GetHeadPosition`，或其他成员函数调用。  
  
### <a name="return-value"></a>返回值  
 请参阅的返回值描述[GetHead](#gethead)。  
  
### <a name="remarks"></a>备注  
 可以使用`GetNext`中如果建立调用一次的初始位置的向前迭代循环`GetHeadPosition`或`Find`。  
  
 您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。  
  
 如果检索的元素的是在列表中，最后再的新值*rPosition*设置为 NULL。  
  
 就可以执行迭代的过程中删除元素。 有关示例，请参阅[RemoveAt](#removeat)。  
  
> [!NOTE]
>  MFC 8.0 截至此方法的 const 版本已更改为返回`const CObject*`而不是`const CObject*&`。  此更改是为了使编译器符合 c + + 标准。  
  
 下表显示其他成员函数类似于`CObList::GetNext`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]  
  
 此程序的结果如下所示：  
  
 `a CAge at $479C 40`  
  
 `a CAge at $46C0 21`  
  
##  <a name="getprev"></a>  CObList::GetPrev  
 获取标识的列表元素*rPosition*，然后设置*rPosition*列表的上一项的位置值。  
  
```  
CObject*& GetPrev(POSITION& rPosition);  
const CObject* GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 *rPosition*  
 对先前返回的位置值的引用`GetPrev`或其他成员函数调用。  
  
### <a name="return-value"></a>返回值  
 请参阅的返回值描述[GetHead](#gethead)。  
  
### <a name="remarks"></a>备注  
 可以使用`GetPrev`在反向迭代循环中，如果建立初始位置通过调用`GetTailPosition`或`Find`。  
  
 您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。  
  
 如果检索的元素的为第一个在列表中，则新值的*rPosition*设置为 NULL。  
  
> [!NOTE]
>  MFC 8.0 截至此方法的 const 版本已更改为返回`const CObject*`而不是`const CObject*&`。  此更改是为了使编译器符合 c + + 标准。  
  
 下表显示其他成员函数类似于`CObList::GetPrev`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]  
  
 此程序的结果如下所示：  
  
 `a CAge at $421C 21`  
  
 `a CAge at $421C 40`  
  
##  <a name="getsize"></a>  CObList::GetSize  
 返回列表的元素数。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表中的项数。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索列表中的元素数。  
  
 下表显示其他成员函数类似于`CObList::GetSize`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize （) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]  
  
##  <a name="gettail"></a>  CObList::GetTail  
 获取`CObject`表示此列表的结尾元素的指针。  
  
```  
CObject*& GetTail();  
const CObject*& GetTail() const;  
```  
  
### <a name="return-value"></a>返回值  
 请参阅的返回值描述[GetHead](#gethead)。  
  
### <a name="remarks"></a>备注  
 必须确保该列表不是空之前调用`GetTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
 下表显示其他成员函数类似于`CObList::GetTail`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetTail （) const; void\*& GetTail （);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetTail （) const;CString & GetTail （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]  
  
##  <a name="gettailposition"></a>  CObList::GetTailPosition  
 获取此列表; 结尾元素的位置**NULL**如果列表为空。  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 可用于迭代或检索对象指针; 一个位置值如果列表为空，则为 NULL。  
  
 下表显示其他成员函数类似于`CObList::GetTailPosition`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 GetTailPosition （) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 GetTailPosition （) const;**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]  
  
##  <a name="insertafter"></a>  CObList::InsertAfter  
 在指定位置处的元素后添加到此列表的一个元素。  
  
```  
POSITION InsertAfter(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 返回先前的位置值`GetNext`， `GetPrev`，或`Find`成员函数调用。  
  
 *newElement*  
 要添加到此列表的对象指针。  
  
 下表显示其他成员函数类似于`CObList::InsertAfter`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 InsertAfter (位置***位置* **，void** <strong>\*</strong> `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 InsertAfter (位置***位置* **，const CString &** `newElement` **);**<br /><br /> **位置 InsertAfter (位置***位置* **，LPCTSTR** `newElement` **);**|  
  
### <a name="return-value"></a>返回值  
 相同的位置值作为*位置*参数。  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]  
  
 此程序的结果如下所示：  
  
 `InsertAfter example: A CObList with 3 elements`  
  
 `a CAge at $4A44 40`  
  
 `a CAge at $4A64 65`  
  
 `a CAge at $4968 21`  
  
##  <a name="insertbefore"></a>  CObList::InsertBefore  
 将元素添加到此列表中指定位置处的元素之前。  
  
```  
POSITION InsertBefore(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 返回先前的位置值`GetNext`， `GetPrev`，或`Find`成员函数调用。  
  
 *newElement*  
 要添加到此列表的对象指针。  
  
### <a name="return-value"></a>返回值  
 可用于迭代或检索对象指针; 一个位置值如果列表为空，则为 NULL。  
  
 下表显示其他成员函数类似于`CObList::InsertBefore`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 InsertBefore (位置***位置* **，void** <strong>\*</strong> `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 InsertBefore (位置***位置* **，const CString &** `newElement` **);**<br /><br /> **位置 InsertBefore (位置***位置* **，LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]  
  
 此程序的结果如下所示：  
  
 `InsertBefore example: A CObList with 3 elements`  
  
 `a CAge at $4AE2 40`  
  
 `a CAge at $4B02 65`  
  
 `a CAge at $49E6 21`  
  
##  <a name="isempty"></a>  CObList::IsEmpty  
 指示此列表是否包含任何元素。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果此列表为空，则为非零值否则为 0。  
  
 下表显示其他成员函数类似于`CObList::IsEmpty`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty （) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty （) const;**|  
  
### <a name="example"></a>示例  
  有关示例，请参阅[RemoveAll](#removeall)。  
  
##  <a name="removeall"></a>  CObList::RemoveAll  
 从此列表中移除所有元素，并释放关联`CObList`内存。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 如果列表已为空，则会不生成任何错误。  
  
 删除中的元素时`CObList`，从列表中删除对象指针。 它由你负责删除对象本身。  
  
 下表显示其他成员函数类似于`CObList::RemoveAll`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll （);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]  
  
##  <a name="removeat"></a>  CObList::RemoveAt  
 此列表中移除指定的元素。  
  
```  
void RemoveAt(POSITION position);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 若要从列表中移除的元素的位置。  
  
### <a name="remarks"></a>备注  
 删除元素时`CObList`，从列表中删除的对象指针。 它由你负责删除对象本身。  
  
 您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。  
  
 下表显示其他成员函数类似于`CObList::RemoveAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (位置***位置* **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (位置***位置* **);**|  
  
### <a name="example"></a>示例  
  列表迭代过程中删除元素时要小心。 下面的示例演示一种删除方法，可保证是有效**位置**值[GetNext](#getnext)。  
  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]  
  
 此程序的结果如下所示：  
  
 `RemoveAt example: A CObList with 2 elements`  
  
 `a CAge at $4C1E 65`  
  
 `a CAge at $4B22 21`  
  
##  <a name="removehead"></a>  CObList::RemoveHead  
 从列表的开头移除的元素并返回的指针。  
  
```  
CObject* RemoveHead();
```  
  
### <a name="return-value"></a>返回值  
 `CObject`以前位于列表的开头的指针。  
  
### <a name="remarks"></a>备注  
 必须确保该列表不是空之前调用`RemoveHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
 下表显示其他成员函数类似于`CObList::RemoveHead`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead （);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]  
  
##  <a name="removetail"></a>  CObList::RemoveTail  
 从列表的结尾移除的元素并返回的指针。  
  
```  
CObject* RemoveTail();
```  
  
### <a name="return-value"></a>返回值  
 指向所列表的结尾处的对象的指针。  
  
### <a name="remarks"></a>备注  
 必须确保该列表不是空之前调用`RemoveTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
 下表显示其他成员函数类似于`CObList::RemoveTail`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail （);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail （);**|  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]  
  
##  <a name="setat"></a>  CObList::SetAt  
 设置给定位置处的元素。  
  
```  
void SetAt(
    POSITION pos,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>参数  
 *pos*  
 若要设置的元素的位置。  
  
 *newElement*  
 `CObject`用于写入到列表的指针。  
  
### <a name="remarks"></a>备注  
 位置类型的变量是列表的键。 不是索引，请与相同和您无法对位置值自己。 `SetAt` 写入`CObject`到列表中的指定位置的指针。  
  
 您必须确保你的位置值表示在列表中的有效位置。 如果无效，Microsoft 基础类库的调试版本断言。  
  
 下表显示其他成员函数类似于`CObList::SetAt`。  
  
|类|成员函数|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (位置** `pos` **，const CString &** `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt (位置** `pos` **，LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>示例  
  请参阅[CObList::CObList](#coblist)有关的列表`CAge`类。  
  
 [!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]  
  
 此程序的结果如下所示：  
  
 `SetAt example: A CObList with 2 elements`  
  
 `a CAge at $4D98 40`  
  
 `a CAge at $4DB8 65`  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CStringList 类](../../mfc/reference/cstringlist-class.md)   
 [CPtrList 类](../../mfc/reference/cptrlist-class.md)
