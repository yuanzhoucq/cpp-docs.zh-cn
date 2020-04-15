---
title: C字节类
ms.date: 11/04/2016
f1_keywords:
- CByteArray
- AFXCOLL/CByteArray
- AFXCOLL/CByteArray::CByteArray
- AFXCOLL/CByteArray::Add
- AFXCOLL/CByteArray::Append
- AFXCOLL/CByteArray::Copy
- AFXCOLL/CByteArray::ElementAt
- AFXCOLL/CByteArray::FreeExtra
- AFXCOLL/CByteArray::GetAt
- AFXCOLL/CByteArray::GetCount
- AFXCOLL/CByteArray::GetData
- AFXCOLL/CByteArray::GetSize
- AFXCOLL/CByteArray::GetUpperBound
- AFXCOLL/CByteArray::InsertAt
- AFXCOLL/CByteArray::IsEmpty
- AFXCOLL/CByteArray::RemoveAll
- AFXCOLL/CByteArray::RemoveAt
- AFXCOLL/CByteArray::SetAt
- AFXCOLL/CByteArray::SetAtGrow
- AFXCOLL/CByteArray::SetSize
helpviewer_keywords:
- CByteArray [MFC], CByteArray
- CByteArray [MFC], Add
- CByteArray [MFC], Append
- CByteArray [MFC], Copy
- CByteArray [MFC], ElementAt
- CByteArray [MFC], FreeExtra
- CByteArray [MFC], GetAt
- CByteArray [MFC], GetCount
- CByteArray [MFC], GetData
- CByteArray [MFC], GetSize
- CByteArray [MFC], GetUpperBound
- CByteArray [MFC], InsertAt
- CByteArray [MFC], IsEmpty
- CByteArray [MFC], RemoveAll
- CByteArray [MFC], RemoveAt
- CByteArray [MFC], SetAt
- CByteArray [MFC], SetAtGrow
- CByteArray [MFC], SetSize
ms.assetid: 53d4a512-657c-4187-9609-e3f5339a78e0
ms.openlocfilehash: 9da30f6546a69a51c56bf4b27668e1603c13290b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352385"
---
# <a name="cbytearray-class"></a>C字节类

支持字节的动态数组。

## <a name="syntax"></a>语法

```
class CByteArray : public CObject
```

## <a name="members"></a>成员

的成员`CByteArray`函数类似于类[CObarray](../../mfc/reference/cobarray-class.md)的成员函数。 由于此相似性，因此你可以使用 `CObArray` 参考文档获取成员函数细节。 无论将`CObject`指针视为函数参数或返回值，请替换 BYTE。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，转换为

`BYTE CByteArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C字节数组：C字节数组](../../mfc/reference/cobarray-class.md#cobarray)|构造一个空数组。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C字节数组：：添加](../../mfc/reference/cobarray-class.md#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CByteArray：：追加](../../mfc/reference/cobarray-class.md#append)|将另一个数组追加到该数组中；根据需要扩展该数组。|
|[C字节数组：复制](../../mfc/reference/cobarray-class.md#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CBytearray：：元素](../../mfc/reference/cobarray-class.md#elementat)|返回对数组中的字节的临时引用。|
|[CBytearray：免费额外](../../mfc/reference/cobarray-class.md#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[CBytearray：GetAt](../../mfc/reference/cobarray-class.md#getat)|返回给定索引位置处的值。|
|[C字节数组：获取计数](../../mfc/reference/cobarray-class.md#getcount)|获取此数组中的元素数。|
|[C字节数组：获取数据](../../mfc/reference/cobarray-class.md#getdata)|允许访问该数组中的元素。 可以为 NULL。|
|[CBytearray：获取 Size](../../mfc/reference/cobarray-class.md#getsize)|获取此数组中的元素数。|
|[CBytearray：获取上乘](../../mfc/reference/cobarray-class.md#getupperbound)|返回最大的有效索引。|
|[C字节数组：：插入At](../../mfc/reference/cobarray-class.md#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CBytearray：：空](../../mfc/reference/cobarray-class.md#isempty)|确定数组是否为空。|
|[CBytearray：：删除所有](../../mfc/reference/cobarray-class.md#removeall)|从此数组中移除所有元素。|
|[C字节数组：：删除AT](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引处的元素。|
|[CBytearray：setat](../../mfc/reference/cobarray-class.md#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CBytearray：：Setat增长](../../mfc/reference/cobarray-class.md#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[C字节数组：：设置大小](../../mfc/reference/cobarray-class.md#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CByteArray：：运算符\[\]](../../mfc/reference/cobarray-class.md#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

`CByteArray`合并IMPLEMENT_SERIAL宏以支持其元素的序列化和转储。 如果将字节数组存储在存档中，无论是使用重载插入 （ **<<**） 运算符还是使用`Serialize`成员函数，则每个元素依次序列化。

> [!NOTE]
> 在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

如果需要从数组中的各个元素调试输出，则必须将`CDumpContext`对象的深度设置为 1 或更大。

有关使用`CByteArray`的详细信息，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CByteArray`

## <a name="requirements"></a>要求

**标题：** afxcoll.h

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CObArray 类](../../mfc/reference/cobarray-class.md)
