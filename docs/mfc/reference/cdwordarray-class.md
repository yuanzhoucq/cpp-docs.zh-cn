---
title: CDWordArray 类
ms.date: 11/04/2016
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
- AFXCOLL/CDWordArray::CDWordArray
- AFXCOLL/CDWordArray::Add
- AFXCOLL/CDWordArray::Append
- AFXCOLL/CDWordArray::Copy
- AFXCOLL/CDWordArray::ElementAt
- AFXCOLL/CDWordArray::FreeExtra
- AFXCOLL/CDWordArray::GetAt
- AFXCOLL/CDWordArray::GetCount
- AFXCOLL/CDWordArray::GetData
- AFXCOLL/CDWordArray::GetSize
- AFXCOLL/CDWordArray::GetUpperBound
- AFXCOLL/CDWordArray::InsertAt
- AFXCOLL/CDWordArray::IsEmpty
- AFXCOLL/CDWordArray::RemoveAll
- AFXCOLL/CDWordArray::RemoveAt
- AFXCOLL/CDWordArray::SetAt
- AFXCOLL/CDWordArray::SetAtGrow
- AFXCOLL/CDWordArray::SetSize
helpviewer_keywords:
- CDWordArray [MFC], CDWordArray
- CDWordArray [MFC], Add
- CDWordArray [MFC], Append
- CDWordArray [MFC], Copy
- CDWordArray [MFC], ElementAt
- CDWordArray [MFC], FreeExtra
- CDWordArray [MFC], GetAt
- CDWordArray [MFC], GetCount
- CDWordArray [MFC], GetData
- CDWordArray [MFC], GetSize
- CDWordArray [MFC], GetUpperBound
- CDWordArray [MFC], InsertAt
- CDWordArray [MFC], IsEmpty
- CDWordArray [MFC], RemoveAll
- CDWordArray [MFC], RemoveAt
- CDWordArray [MFC], SetAt
- CDWordArray [MFC], SetAtGrow
- CDWordArray [MFC], SetSize
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
ms.openlocfilehash: e009ca3e3612d10d9cdf62d4bea32224f7b7522c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373999"
---
# <a name="cdwordarray-class"></a>CDWordArray 类

支持 32 位双字数组。

## <a name="syntax"></a>语法

```
class CDWordArray : public CObject
```

## <a name="members"></a>成员

的成员`CDWordArray`函数类似于类[CObarray](../../mfc/reference/cobarray-class.md)的成员函数。 由于此相似性，因此你可以使用 `CObArray` 参考文档获取成员函数细节。 在将`CObject`指针视为函数参数或返回值的位置，请替换 。 `DWORD`

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，转换为

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDWordArray：CDWordArray](../../mfc/reference/cobarray-class.md#cobarray)|构造一个空数组。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDWordArray：：添加](../../mfc/reference/cobarray-class.md#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CDWordArray：：附加](../../mfc/reference/cobarray-class.md#append)|将另一个数组追加到该数组中；根据需要扩展该数组。|
|[CDWordArray：复制](../../mfc/reference/cobarray-class.md#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CDWordArray：：元素](../../mfc/reference/cobarray-class.md#elementat)|返回对数组中的字节的临时引用。|
|[CDWordArray：：免费额外](../../mfc/reference/cobarray-class.md#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[CDWordArray：获取At](../../mfc/reference/cobarray-class.md#getat)|返回给定索引位置处的值。|
|[CDWordArray：获取计数](../../mfc/reference/cobarray-class.md#getcount)|获取此数组中的元素数。|
|[CDWordArray：获取数据](../../mfc/reference/cobarray-class.md#getdata)|允许访问该数组中的元素。 可以为 NULL。|
|[CDWordArray：获取Size](../../mfc/reference/cobarray-class.md#getsize)|获取此数组中的元素数。|
|[CDWordArray：获取上部](../../mfc/reference/cobarray-class.md#getupperbound)|返回最大的有效索引。|
|[CDWordArray：：插入At](../../mfc/reference/cobarray-class.md#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CDWordArray：：是空的](../../mfc/reference/cobarray-class.md#isempty)|确定数组是否为空。|
|[CDWordArray：：删除所有](../../mfc/reference/cobarray-class.md#removeall)|从此数组中移除所有元素。|
|[CDWordArray：：删除At](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引处的元素。|
|[CDWordArray：：Setat](../../mfc/reference/cobarray-class.md#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CDWordArray：：Setat增长](../../mfc/reference/cobarray-class.md#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[CDWordArray：：设置大小](../../mfc/reference/cobarray-class.md#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CDWordArray：：运算符\[\]](../../mfc/reference/cobarray-class.md#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

`CDWordArray` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。 如果将双字数组存储在存档中，则使用重载插入 （ **<<**） 运算符或`Serialize`成员函数，则每个元素依次序列化。

> [!NOTE]
> 在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

如果需要从数组中的各个元素调试输出，则必须将`CDumpContext`对象的深度设置为 1 或更大。

有关使用`CDWordArray`的详细信息，请参阅文章[集合](../../mfc/collections.md)。

## <a name="requirements"></a>要求

**标题：** afxcoll.h

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CObArray 类](../../mfc/reference/cobarray-class.md)
