---
title: "CList 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- lists
- lists, base class for
- CList class
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 05d35419f70ab039e6981938c516201b252878d4
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="clist-class"></a>CList 类
支持可按顺序或值访问的不唯一对象的有序列表。  
  
## <a name="syntax"></a>语法  
  
```  
template<class TYPE, class ARG_TYPE = const TYPE&>  
class CList : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CList::CList](#clist)|构造空的有序列的表。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CList::AddHead](#addhead)|将一个元素 （或另一个列表中的所有元素） 添加到 （会生成新的头） 的列表的开头。|  
|[CList::AddTail](#addtail)|将一个元素 （或另一个列表中的所有元素） 添加到 （会生成新的结尾） 列表的末尾。|  
|[CList::Find](#find)|获取指针值所指定的元素的位置。|  
|[CList::FindIndex](#findindex)|获取指定的元素的从零开始的索引位置。|  
|[CList::GetAt](#getat)|获取位于给定位置的元素。|  
|[CList::GetCount](#getcount)|返回此列表中的元素数。|  
|[CList::GetHead](#gethead)|返回的列表 （不能为空） 的头元素。|  
|[CList::GetHeadPosition](#getheadposition)|返回列表的头元素的位置。|  
|[CList::GetNext](#getnext)|获取用于循环的下一个元素。|  
|[CList::GetPrev](#getprev)|获取循环访问的上一个元素。|  
|[CList::GetSize](#getsize)|返回此列表中的元素数。|  
|[CList::GetTail](#gettail)|返回 （不能为空） 的列表的结尾元素。|  
|[CList::GetTailPosition](#gettailposition)|返回列表的结尾元素的位置。|  
|[CList::InsertAfter](#insertafter)|在给定位置后插入一个新元素。|  
|[CList::InsertBefore](#insertbefore)|将插入一个新的给定位置之前的元素。|  
|[CList::IsEmpty](#isempty)|空列表条件 （元素） 的的测试。|  
|[CList::RemoveAll](#removeall)|从此列表中移除所有元素。|  
|[CList::RemoveAt](#removeat)|从此列表中，指定位置移除的元素。|  
|[CList::RemoveHead](#removehead)|从列表头中移除的元素。|  
|[CList::RemoveTail](#removetail)|从列表的结尾移除的元素。|  
|[CList::SetAt](#setat)|设置给定位置的元素。|  
  
#### <a name="parameters"></a>参数  
 `TYPE`  
 在列表中存储对象的类型。  
  
 `ARG` *_* `TYPE`  
 用于引用存储在列表中的对象的类型。 可以为引用。  
  
## <a name="remarks"></a>备注  
 `CList`列表类似于双向链接列表。  
  
 类型的变量**位置**至关重要的列表。 您可以使用**位置**变量作为表按顺序中遍历的迭代器和一个书签以保存一个位置。 位置并不相同索引，但是。  
  
 插入元素非常快速位于列表的头、 尾和已知**位置**。 顺序搜索则需要按值或索引查找元素。 此搜索速度较慢，如果列表太长。  
  
 如果您需要在列表中的各个元素的转储，必须将转储上下文的深度设置为 1 或更高。  
  
 此类调用全局帮助器函数的某些成员函数必须进行自定义的大部分使用`CList`类。 请参阅[集合类帮助器](../../mfc/reference/collection-class-helpers.md)"宏和全局变量"部分中。  
  
 有关详细信息使用`CList`，请参阅文章[集合](../../mfc/collections.md)。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&35;](../../mfc/codesnippet/cpp/clist-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CList`  
  
## <a name="requirements"></a>要求  
 **标头：** afxtempl.h  
  
##  <a name="addhead"></a>CList::AddHead  
 将新元素的列表添加到此列表的开头。  
  
```  
POSITION AddHead(ARG_TYPE newElement);  
void AddHead(CList* pNewList);
```  
  
### <a name="parameters"></a>参数  
 `ARG_TYPE`  
 用于指定列表元素类型的模板参数（可以为一个引用）。  
  
 `newElement`  
 新元素。  
  
 `pNewList`  
 一个指向另一个`CList`列表。 中的元素`pNewList`将添加到此列表。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回**位置**新插入的元素的值。  
  
### <a name="remarks"></a>备注  
 列表可以为空操作之前。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&36;](../../mfc/codesnippet/cpp/clist-class_2.cpp)]  
  
##  <a name="addtail"></a>CList::AddTail  
 将新元素的列表添加到此列表的末尾。  
  
```  
POSITION AddTail(ARG_TYPE newElement);  
void AddTail(CList* pNewList);
```  
  
### <a name="parameters"></a>参数  
 `ARG_TYPE`  
 用于指定列表元素类型的模板参数（可以为一个引用）。  
  
 `newElement`  
 要添加到此列表的元素。  
  
 `pNewList`  
 一个指向另一个`CList`列表。 中的元素`pNewList`将添加到此列表。  
  
### <a name="return-value"></a>返回值  
 第一个版本返回**位置**新插入的元素的值。  
  
### <a name="remarks"></a>备注  
 列表可以为空操作之前。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&37;](../../mfc/codesnippet/cpp/clist-class_3.cpp)]  
  
##  <a name="clist"></a>CList::CList  
 构造空的有序列的表。  
  
```  
CList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>参数  
 `nBlockSize`  
 扩展列表的内存分配粒度。  
  
### <a name="remarks"></a>备注  
 当列表的增长，单位为分配内存`nBlockSize`条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&38;](../../mfc/codesnippet/cpp/clist-class_4.cpp)]  
  
##  <a name="find"></a>CList::Find  
 按顺序来查找与指定的第一个元素在列表中搜索`searchValue`。  
  
```  
POSITION Find(
    ARG_TYPE searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 `ARG_TYPE`  
 用于指定列表元素类型的模板参数（可以为一个引用）。  
  
 `searchValue`  
 要在列表中找到的值。  
  
 `startAfter`  
 搜索起始位置。 如果未不指定任何值，那么搜索将开始与头元素。  
  
### <a name="return-value"></a>返回值  
 一个**位置**可以用于迭代或检索对象指针; 值**NULL**如果未找到的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&39;](../../mfc/codesnippet/cpp/clist-class_5.cpp)]  
  
##  <a name="findindex"></a>CList::FindIndex  
 使用值为`nIndex`作为列表的索引。  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要找的列表中元素的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 一个**位置**可以用于迭代或检索对象指针; 值**NULL**如果`nIndex`为负数或过大。  
  
### <a name="remarks"></a>备注  
 它从列表中，停止上的开头开始按顺序进行扫描*n*th 元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&40;](../../mfc/codesnippet/cpp/clist-class_6.cpp)]  
  
##  <a name="getat"></a>CList::GetAt  
 获取位于给定位置列表元素。  
  
```  
TYPE& GetAt(POSITION position);  
const TYPE& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数列表中的指定对象的类型。  
  
 *位置*  
 要获取的元素的列表中的位置。  
  
### <a name="return-value"></a>返回值  
 请参见的返回值说明`GetHead`。  
  
### <a name="remarks"></a>备注  
 `GetAt`返回与给定位置关联的元素 （或元素的引用）。 它不同时，作为一种索引，并不能对操作**位置**您自己的值。 类型的变量**位置**至关重要的列表。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
### <a name="example"></a>示例  
  请参阅示例[CList::GetHeadPosition](#getheadposition)。  
  
##  <a name="getcount"></a>CList::GetCount  
 获取此列表中的元素数。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个包含元素计数的整数值。  
  
### <a name="remarks"></a>备注  
 调用此方法将生成相同的结果[CList::GetSize](#getsize)方法。  
  
### <a name="example"></a>示例  
  请参阅示例[CList::RemoveHead](#removehead)。  
  
##  <a name="gethead"></a>CList::GetHead  
 获取此列表的头元素 （或与头元素的引用）。  
  
```  
const TYPE& GetHead() const;  
  
TYPE& GetHead();
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数列表中的指定对象的类型。  
  
### <a name="return-value"></a>返回值  
 如果列表为**const**，`GetHead`返回列表的开头处的元素的副本。 这允许要使用仅在赋值语句的右侧的函数，并防止修改列表。  
  
 如果该列表不是**const**，`GetHead`返回对列表的开头处的元素的引用。 这允许在赋值语句的每一端上使用的函数，因此允许列表条目，以进行修改。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`GetHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&41;](../../mfc/codesnippet/cpp/clist-class_7.cpp)]  
  
##  <a name="getheadposition"></a>CList::GetHeadPosition  
 获取此列表的头元素的位置。  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**可以用于迭代或检索对象指针; 值**NULL**如果列表为空。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&42;](../../mfc/codesnippet/cpp/clist-class_8.cpp)]  
  
##  <a name="getnext"></a>CList::GetNext  
 获取标识的列表元素`rPosition`，然后设置`rPosition`到**位置**列表中的下一个条目的值。  
  
```  
TYPE& GetNext(POSITION& rPosition);  
const TYPE& GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数列表中的指定元素的类型。  
  
 `rPosition`  
 对引用**位置**返回先前值`GetNext`， [GetHeadPosition](#getheadposition)，或其他成员函数调用。  
  
### <a name="return-value"></a>返回值  
 如果列表为**const**，`GetNext`返回列表中的元素的副本。 这允许要使用仅在赋值语句的右侧的函数，并防止修改列表。  
  
 如果该列表不是**const**，`GetNext`返回对列表中的元素的引用。 这允许在赋值语句的每一端上使用的函数，因此允许列表条目，以进行修改。  
  
### <a name="remarks"></a>备注  
 您可以使用`GetNext`在向前迭代循环中，如果您建立的初始位置，通过调用`GetHeadPosition`或**查找**。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 如果检索的元素则在列表中，最后的新值`rPosition`设置为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&43;](../../mfc/codesnippet/cpp/clist-class_9.cpp)]  
  
##  <a name="getprev"></a>CList::GetPrev  
 获取标识的列表元素`rPosition`，然后设置`rPosition`到**位置**以前在列表中项的值。  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
const TYPE& GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数列表中的指定元素的类型。  
  
 `rPosition`  
 对引用**位置**返回先前值`GetPrev`或其他成员函数调用。  
  
### <a name="return-value"></a>返回值  
 如果列表为**const**，`GetPrev`返回列表的开头处的元素的副本。 这允许要使用仅在赋值语句的右侧的函数，并防止修改列表。  
  
 如果该列表不是**const**，`GetPrev`返回对列表中的元素的引用。 这允许在赋值语句的每一端上使用的函数，因此允许列表条目，以进行修改。  
  
### <a name="remarks"></a>备注  
 您可以使用`GetPrev`在反向迭代循环中，如果您建立的初始位置，通过调用`GetTailPosition`或**查找**。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
 如果检索的元素则在列表中，第一个的新值`rPosition`设置为**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&44;](../../mfc/codesnippet/cpp/clist-class_10.cpp)]  
  
##  <a name="getsize"></a>CList::GetSize  
 返回列表中元素的数目。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表中的项数。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索列表中的元素数。  调用此方法将生成相同的结果[CList::GetCount](#getcount)方法。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&45;](../../mfc/codesnippet/cpp/clist-class_11.cpp)]  
  
##  <a name="gettail"></a>CList::GetTail  
 获取`CObject`表示此列表的结尾元素的指针。  
  
```  
TYPE& GetTail();  
const TYPE& GetTail() const;  
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数列表中的指定元素的类型。  
  
### <a name="return-value"></a>返回值  
 请参见的返回值说明[GetHead](../../mfc/reference/coblist-class.md#gethead)。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`GetTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)验证列表中包含的元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&46;](../../mfc/codesnippet/cpp/clist-class_12.cpp)]  
  
##  <a name="gettailposition"></a>CList::GetTailPosition  
 获取此列表; 结尾元素的位置**NULL**如果列表为空。  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**可以用于迭代或检索对象指针; 值**NULL**如果列表为空。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&47;](../../mfc/codesnippet/cpp/clist-class_13.cpp)]  
  
##  <a name="insertafter"></a>CList::InsertAfter  
 在指定位置处的元素后，请向此列表中添加一个元素。  
  
```  
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 一个由先前 **、** 或 `GetNext`Find `GetPrev`成员函数调用返回的 **位置** 值。  
  
 `ARG_TYPE`  
 指定列表元素的类型的模板参数。  
  
 `newElement`  
 要添加到此列表的元素。  
  
### <a name="return-value"></a>返回值  
 一个可以用于迭代或列表元素检索的 **位置** 值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&48;](../../mfc/codesnippet/cpp/clist-class_14.cpp)]  
  
##  <a name="insertbefore"></a>CList::InsertBefore  
 将元素添加到此列表中指定位置处的元素之前。  
  
```  
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 一个由先前 **、** 或 `GetNext`Find `GetPrev`成员函数调用返回的 **位置** 值。  
  
 `ARG_TYPE`  
 用于指定列表元素类型的模板参数（可以为一个引用）。  
  
 `newElement`  
 要添加到此列表的元素。  
  
### <a name="return-value"></a>返回值  
 一个可以用于迭代或列表元素检索的 **位置** 值。  
  
### <a name="remarks"></a>备注  
 如果 *position* 为 **NULL**，则该元素插入到了列表的开头。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&49;](../../mfc/codesnippet/cpp/clist-class_15.cpp)]  
  
##  <a name="isempty"></a>CList::IsEmpty  
 指示此列表是否包含任何元素。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果此列表为空，则为非零值否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&50;](../../mfc/codesnippet/cpp/clist-class_16.cpp)]  
  
##  <a name="removeall"></a>CList::RemoveAll  
 从此列表中移除所有元素，并释放关联的内存。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
 如果列表已为空，则会不生成任何错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&51;](../../mfc/codesnippet/cpp/clist-class_17.cpp)]  
  
##  <a name="removeat"></a>CList::RemoveAt  
 从此列表中移除指定的元素。  
  
```  
void RemoveAt(POSITION position);
```  
  
### <a name="parameters"></a>参数  
 *位置*  
 要从列表中移除的元素的位置。  
  
### <a name="remarks"></a>备注  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&52;](../../mfc/codesnippet/cpp/clist-class_18.cpp)]  
  
##  <a name="removehead"></a>CList::RemoveHead  
 从列表头中移除的元素并将指针返回到它。  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数列表中的指定元素的类型。  
  
### <a name="return-value"></a>返回值  
 以前位于列表的开头处的元素。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`RemoveHead`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&53;](../../mfc/codesnippet/cpp/clist-class_19.cpp)]  
  
##  <a name="removetail"></a>CList::RemoveTail  
 从列表的结尾移除的元素并将指针返回到它。  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>参数  
 *类型*  
 模板参数列表中的指定元素的类型。  
  
### <a name="return-value"></a>返回值  
 在列表末尾的元素。  
  
### <a name="remarks"></a>备注  
 您必须确保列表不为空，然后调用`RemoveTail`。 如果列表为空，Microsoft 基础类库的调试版本断言。 使用[IsEmpty](#isempty)验证列表中包含的元素。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&54;](../../mfc/codesnippet/cpp/clist-class_20.cpp)]  
  
##  <a name="setat"></a>CList::SetAt  
 类型的变量**位置**至关重要的列表。  
  
```  
void SetAt(POSITION pos, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 **位置**要设置的元素。  
  
 `ARG_TYPE`  
 用于指定列表元素类型的模板参数（可以为一个引用）。  
  
 `newElement`  
 要添加到列表的元素。  
  
### <a name="remarks"></a>备注  
 它不同时，作为一种索引，并不能对操作**位置**您自己的值。 `SetAt`将元素写入列表中的指定位置。  
  
 您必须确保您**位置**值表示列表中的有效位置。 如果该值无效，Microsoft 基础类库的调试版本断言。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&55;](../../mfc/codesnippet/cpp/clist-class_21.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例收集](../../visual-cpp-samples.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMap 类](../../mfc/reference/cmap-class.md)   
 [CArray 类](../../mfc/reference/carray-class.md)

