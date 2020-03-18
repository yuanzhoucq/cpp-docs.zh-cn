---
title: CStringArray 类
ms.date: 11/04/2016
f1_keywords:
- CStringArray
- AFXCOLL/CStringArray
- AFXCOLL/CStringArray::CStringArray
- AFXCOLL/CStringArray::Add
- AFXCOLL/CStringArray::Append
- AFXCOLL/CStringArray::Copy
- AFXCOLL/CStringArray::ElementAt
- AFXCOLL/CStringArray::FreeExtra
- AFXCOLL/CStringArray::GetAt
- AFXCOLL/CStringArray::GetCount
- AFXCOLL/CStringArray::GetData
- AFXCOLL/CStringArray::GetSize
- AFXCOLL/CStringArray::GetUpperBound
- AFXCOLL/CStringArray::InsertAt
- AFXCOLL/CStringArray::IsEmpty
- AFXCOLL/CStringArray::RemoveAll
- AFXCOLL/CStringArray::RemoveAt
- AFXCOLL/CStringArray::SetAt
- AFXCOLL/CStringArray::SetAtGrow
- AFXCOLL/CStringArray::SetSize
helpviewer_keywords:
- CStringArray [MFC], CStringArray
- CStringArray [MFC], Add
- CStringArray [MFC], Append
- CStringArray [MFC], Copy
- CStringArray [MFC], ElementAt
- CStringArray [MFC], FreeExtra
- CStringArray [MFC], GetAt
- CStringArray [MFC], GetCount
- CStringArray [MFC], GetData
- CStringArray [MFC], GetSize
- CStringArray [MFC], GetUpperBound
- CStringArray [MFC], InsertAt
- CStringArray [MFC], IsEmpty
- CStringArray [MFC], RemoveAll
- CStringArray [MFC], RemoveAt
- CStringArray [MFC], SetAt
- CStringArray [MFC], SetAtGrow
- CStringArray [MFC], SetSize
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
ms.openlocfilehash: f5be5f44e86e3e24bc51dc014ca3c837bf5cf07d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445121"
---
# <a name="cstringarray-class"></a>CStringArray 类

支持[CString](../../atl-mfc-shared/using-cstring.md)对象的数组。

## <a name="syntax"></a>语法

```
class CStringArray : public CObject
```

## <a name="members"></a>Members

`CStringArray` 的成员函数类似于类[CObArray](../../mfc/reference/cobarray-class.md)的成员函数。 由于此相似性，因此你可以使用 `CObArray` 参考文档获取成员函数细节。 无论你在何处看到作为返回值的 `CObject` 指针，都要用[cstring](../../atl-mfc-shared/using-cstring.md)对象（而不是[cstring](../../atl-mfc-shared/using-cstring.md)指针）来替换。 无论你在何处看到作为函数参数的 `CObject` 指针，都请替换 `LPCTSTR`。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，转换为

`CString CStringArray::GetAt( int <nIndex> ) const;`

和

`void SetAt( int <nIndex>, CObject* <newElement> )`

转换为

`void SetAt( int <nIndex>, LPCTSTR <newElement> )`

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CStringArray::CStringArray](../../mfc/reference/cobarray-class.md#cobarray)|构造一个空数组。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CStringArray：： Add](../../mfc/reference/cobarray-class.md#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CStringArray：： Append](../../mfc/reference/cobarray-class.md#append)|将另一个数组追加到该数组中；根据需要扩展该数组。|
|[CStringArray：： Copy](../../mfc/reference/cobarray-class.md#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CStringArray：： .Value.elementat](../../mfc/reference/cobarray-class.md#elementat)|在该数组中返回对元素指针的临时引用。|
|[CStringArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[CStringArray：： GetAt](../../mfc/reference/cobarray-class.md#getat)|返回给定索引位置处的值。|
|[CStringArray：： GetCount](../../mfc/reference/cobarray-class.md#getcount)|获取此数组中的元素数。|
|[CStringArray：：](../../mfc/reference/cobarray-class.md#getdata)|允许访问该数组中的元素。 可以为**NULL**。|
|[CStringArray：： GetSize](../../mfc/reference/cobarray-class.md#getsize)|获取此数组中的元素数。|
|[CStringArray：： System.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)|返回最大的有效索引。|
|[CStringArray：： InsertAt](../../mfc/reference/cobarray-class.md#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CStringArray：： IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|确定数组是否为空。|
|[CStringArray：： RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|从此数组中移除所有元素。|
|[CStringArray：： RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引处的元素。|
|[CStringArray：： SetAt](../../mfc/reference/cobarray-class.md#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CStringArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[CStringArray：： SetSize](../../mfc/reference/cobarray-class.md#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[CStringArray：： operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

`CStringArray` 包含 IMPLEMENT_SERIAL 宏，以支持其元素的序列化和转储。 如果将 `CString` 对象的数组存储到存档中（使用重载插入运算符或 `Serialize` 成员函数），则将依次序列化每个元素。

> [!NOTE]
>  在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

如果你需要对数组中单个字符串元素进行转储，则必须将转储上下文的深度设置为等于或大于 1。

当删除 `CString` 数组或移除其元素时，将以适当方式释放字符串内存。

有关使用 `CStringArray`的详细信息，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CStringArray`

## <a name="requirements"></a>要求

**标头：** afxcoll。h

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
