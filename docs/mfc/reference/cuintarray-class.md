---
title: CUIntArray 类
ms.date: 11/04/2016
f1_keywords:
- CUIntArray
- AFXCOLL/CUIntArray
- AFXCOLL/CUIntArray::CUIntArray
- AFXCOLL/CUIntArray::Add
- AFXCOLL/CUIntArray::Append
- AFXCOLL/CUIntArray::Copy
- AFXCOLL/CUIntArray::ElementAt
- AFXCOLL/CUIntArray::FreeExtra
- AFXCOLL/CUIntArray::GetAt
- AFXCOLL/CUIntArray::GetCount
- AFXCOLL/CUIntArray::GetData
- AFXCOLL/CUIntArray::GetSize
- AFXCOLL/CUIntArray::GetUpperBound
- AFXCOLL/CUIntArray::InsertAt
- AFXCOLL/CUIntArray::IsEmpty
- AFXCOLL/CUIntArray::RemoveAll
- AFXCOLL/CUIntArray::RemoveAt
- AFXCOLL/CUIntArray::SetAt
- AFXCOLL/CUIntArray::SetAtGrow
- AFXCOLL/CUIntArray::SetSize
helpviewer_keywords:
- CUIntArray [MFC], CUIntArray
- CUIntArray [MFC], Add
- CUIntArray [MFC], Append
- CUIntArray [MFC], Copy
- CUIntArray [MFC], ElementAt
- CUIntArray [MFC], FreeExtra
- CUIntArray [MFC], GetAt
- CUIntArray [MFC], GetCount
- CUIntArray [MFC], GetData
- CUIntArray [MFC], GetSize
- CUIntArray [MFC], GetUpperBound
- CUIntArray [MFC], InsertAt
- CUIntArray [MFC], IsEmpty
- CUIntArray [MFC], RemoveAll
- CUIntArray [MFC], RemoveAt
- CUIntArray [MFC], SetAt
- CUIntArray [MFC], SetAtGrow
- CUIntArray [MFC], SetSize
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
ms.openlocfilehash: 9d620269bbf6695af992feaf0df2ef1161c9ae8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373244"
---
# <a name="cuintarray-class"></a>CUIntArray 类

支持无符号整数数组。

## <a name="syntax"></a>语法

```
class CUIntArray : public CObject
```

## <a name="members"></a>成员

的成员`CUIntArray`函数类似于类[CObarray](../../mfc/reference/cobarray-class.md)的成员函数。 由于此相似性，因此你可以使用 `CObArray` 参考文档获取成员函数细节。 无论将`CObject`指针视为函数参数或返回值，请替换 UINT。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，转换为

`UINT CUIntArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CUIntarray：CUIntarray](../../mfc/reference/cobarray-class.md#cobarray)|构造一个空数组。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CUIntarray：添加](../../mfc/reference/cobarray-class.md#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CUIntarray：：附加](../../mfc/reference/cobarray-class.md#append)|将另一个数组追加到该数组中；根据需要扩展该数组。|
|[CUIntarray：复制](../../mfc/reference/cobarray-class.md#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CUIntarray：元素At](../../mfc/reference/cobarray-class.md#elementat)|在该数组中返回对元素指针的临时引用。|
|[CUIntarray：免费额外](../../mfc/reference/cobarray-class.md#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[CUIntarray：Getat](../../mfc/reference/cobarray-class.md#getat)|返回给定索引位置处的值。|
|[CUIntarray：获取计数](../../mfc/reference/cobarray-class.md#getcount)|获取此数组中的元素数。|
|[CUIntarray：获取数据](../../mfc/reference/cobarray-class.md#getdata)|允许访问该数组中的元素。 可以为 NULL。|
|[CUIntarray：获取大小](../../mfc/reference/cobarray-class.md#getsize)|获取此数组中的元素数。|
|[CUIntarray：获取上部](../../mfc/reference/cobarray-class.md#getupperbound)|返回最大的有效索引。|
|[CUIntarray：插入At](../../mfc/reference/cobarray-class.md#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CUIntarray：：空](../../mfc/reference/cobarray-class.md#isempty)|确定数组是否为空。|
|[CUIntarray：删除所有](../../mfc/reference/cobarray-class.md#removeall)|从此数组中移除所有元素。|
|[CUIntarray：删除At](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引处的元素。|
|[CUIntarray：Setat](../../mfc/reference/cobarray-class.md#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CUIntarray：setat增长](../../mfc/reference/cobarray-class.md#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[CUIntarray：设置大小](../../mfc/reference/cobarray-class.md#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CUIntarray：：运算符\[\]](../../mfc/reference/cobarray-class.md#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

无符号整数（UINT）与单词和双字不同，因为 UINT 的物理大小可能会根据目标操作环境而变化。 UINT 的大小与双字相同。

`CUIntArray`合并[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)宏以支持运行时类型访问和转储到[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象。 如果需要单个未签名整数元素的转储，则必须将转储上下文的深度设置为 1 或更大。 无法序列化无符号整数数组。

> [!NOTE]
> 在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

有关使用`CUIntArray`的详细信息，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CUIntArray`

## <a name="requirements"></a>要求

**标题：** afxcoll.h

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
