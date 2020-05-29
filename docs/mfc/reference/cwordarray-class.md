---
title: CWordArray 类
ms.date: 09/07/2019
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CWordArray::CWordArray
- AFXCOLL/CWordArray::Add
- AFXCOLL/CWordArray::Append
- AFXCOLL/CWordArray::Copy
- AFXCOLL/CWordArray::ElementAt
- AFXCOLL/CWordArray::FreeExtra
- AFXCOLL/CWordArray::GetAt
- AFXCOLL/CWordArray::GetCount
- AFXCOLL/CWordArray::GetData
- AFXCOLL/CWordArray::GetSize
- AFXCOLL/CWordArray::GetUpperBound
- AFXCOLL/CWordArray::InsertAt
- AFXCOLL/CWordArray::IsEmpty
- AFXCOLL/CWordArray::RemoveAll
- AFXCOLL/CWordArray::RemoveAt
- AFXCOLL/CWordArray::SetAt
- AFXCOLL/CWordArray::SetAtGrow
- AFXCOLL/CWordArray::SetSize
helpviewer_keywords:
- CWordArray [MFC], CWordArray
- CWordArray [MFC], Add
- CWordArray [MFC], Append
- CWordArray [MFC], Copy
- CWordArray [MFC], ElementAt
- CWordArray [MFC], FreeExtra
- CWordArray [MFC], GetAt
- CWordArray [MFC], GetCount
- CWordArray [MFC], GetData
- CWordArray [MFC], GetSize
- CWordArray [MFC], GetUpperBound
- CWordArray [MFC], InsertAt
- CWordArray [MFC], IsEmpty
- CWordArray [MFC], RemoveAll
- CWordArray [MFC], RemoveAt
- CWordArray [MFC], SetAt
- CWordArray [MFC], SetAtGrow
- CWordArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
ms.openlocfilehash: 9dfb0b674d52b288ebd05bf7574f1ae05e4ed1f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365915"
---
# <a name="cwordarray-class"></a>CWordArray 类

支持 16 位数组。

## <a name="syntax"></a>语法

```
class CWordArray : public CObject
```

## <a name="members"></a>成员

的成员`CWordArray`函数类似于类[CObarray](../../mfc/reference/cobarray-class.md)的成员函数。 由于此相似性，因此你可以使用 `CObArray` 参考文档获取成员函数细节。 无论在哪里看到[CObject](../../mfc/reference/cobject-class.md)指针作为函数参数或返回值，请替换 WORD。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，转换为

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CWordArray：CWordarray](../../mfc/reference/cobarray-class.md#cobarray)|构造一个空数组。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWordArray：添加](../../mfc/reference/cobarray-class.md#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CWordArray：：追加](../../mfc/reference/cobarray-class.md#append)|将另一个数组追加到该数组中；根据需要扩展该数组。|
|[CWordArray：复制](../../mfc/reference/cobarray-class.md#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CWordarray：：元素](../../mfc/reference/cobarray-class.md#elementat)|在该数组中返回对元素指针的临时引用。|
|[CWordArray：：免费额外](../../mfc/reference/cobarray-class.md#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[CWordarray：获取At](../../mfc/reference/cobarray-class.md#getat)|返回给定索引位置处的值。|
|[CWordArray：获取计数](../../mfc/reference/cobarray-class.md#getcount)|获取此数组中的元素数。|
|[CWordArray：获取数据](../../mfc/reference/cobarray-class.md#getdata)|允许访问该数组中的元素。 可以为 NULL。|
|[CWordArray：获取 Size](../../mfc/reference/cobarray-class.md#getsize)|获取此数组中的元素数。|
|[CWordarray：获取上部](../../mfc/reference/cobarray-class.md#getupperbound)|返回最大的有效索引。|
|[CWordarray：：插入At](../../mfc/reference/cobarray-class.md#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CWordarray：：是空的](../../mfc/reference/cobarray-class.md#isempty)|确定数组是否为空。|
|[CWordarray：：删除所有](../../mfc/reference/cobarray-class.md#removeall)|从此数组中移除所有元素。|
|[CWordarray：：删除At](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引处的元素。|
|[CWordarray：setat](../../mfc/reference/cobarray-class.md#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CWordarray：setat增长](../../mfc/reference/cobarray-class.md#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[CWordArray：：设置大小](../../mfc/reference/cobarray-class.md#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CWordArray：运算符 &#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

`CWordArray`合并[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏以支持其元素的序列化和转储。 如果将单词数组存储在存档中，或者使用重载插入运算符或[CObject：序列化](../../mfc/reference/cobject-class.md#serialize)成员函数，则每个元素依次序列化。

> [!NOTE]
> 在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

如果需要数组中单个元素的转储，则必须将转储上下文的深度设置为 1 或更大。

有关使用`CWordArray`的详细信息，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>要求

**标题：** afxcoll.h

## <a name="see-also"></a>另请参阅

[MFC 样品收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
