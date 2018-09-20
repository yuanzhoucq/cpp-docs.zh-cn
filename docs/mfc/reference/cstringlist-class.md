---
title: CStringList 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStringList
- AFXCOLL/CStringList
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
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3182a9f5a53c2f086800eb0eccb7d61e423e591
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439180"
---
# <a name="cstringlist-class"></a>CStringList 类

支持 `CString` 对象列表。

## <a name="syntax"></a>语法

```
class CStringList : public CObject
```

## <a name="members"></a>成员

成员函数`CStringList`类似于类的成员函数[CObList](../../mfc/reference/coblist-class.md)。 由于此相似性，因此你可以使用 `CObList` 参考文档获取成员函数细节。 无论您在何处`CObject`指针作为返回值，替换`CString`(不`CString`指针)。 无论您在何处`CObject`指针作为函数参数，将替换`LPCTSTR`。

`CObject*& CObList::GetHead() const;`

例如，转换为

`CString& CStringList::GetHead() const;`

和

`POSITION AddHead( CObject* <newElement> );`

转换为

`POSITION AddHead( LPCTSTR <newElement> );`

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)|构造一个空列表。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CObList::AddHead](../../mfc/reference/coblist-class.md#addhead)|将一个元素 （或另一个列表中的所有元素） 添加到 （使新头） 了列表的开头。|
|[CObList::AddTail](../../mfc/reference/coblist-class.md#addtail)|将一个元素 （或另一个列表中的所有元素） 添加到列表 （使新结尾） 的尾部。|
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|获取指针值所指定的元素的位置。|
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|获取指定的从零开始的索引的元素的位置。|
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|获取位于给定位置的元素。|
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|返回此列表中的元素数。|
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|返回的列表 （不能为空） 的头元素。|
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|返回列表的头元素的位置。|
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|获取用于循环的下一个元素。|
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|获取循环访问的上一个元素。|
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|返回此列表中的元素数。|
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|返回 （不能为空） 的列表的结尾元素。|
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|返回列表的结尾元素的位置。|
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|在给定位置后插入一个新元素。|
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|将插入新元素之前的给定位置。|
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|对于空列表条件 （元素） 的测试。|
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|此列表中移除所有元素。|
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|从此列表中，指定位置移除一个元素。|
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|从列表的开头移除的元素。|
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|从列表的结尾移除的元素。|
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|设置给定位置处的元素。|

## <a name="remarks"></a>备注

所有比较是都由值，这意味着在字符串中的字符进行比较而不是字符串的地址。

`CStringList` 集成了 IMPLEMENT_SERIAL 宏来支持序列化和转储的它的元素。 如果一系列`CString`对象存储到存档，或者用重载的插入运算符`Serialize`成员函数，每个`CString`反过来序列化元素。

如果你需要个人的转储`CString`元素，必须将转储上下文的深度设置为 1 或更高版本。

有关使用的详细信息`CStringList`，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>要求

**标头：** afxcoll.h

## <a name="see-also"></a>请参阅

[MFC 示例收集](../../visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)



