---
title: CUIntArray 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CUIntArray
- AFXCOLL/CUIntArray
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
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dc9bf5b2a7e7cf5d2335676d9c6fd219ce35634
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064870"
---
# <a name="cuintarray-class"></a>CUIntArray 类

支持无符号整数数组。

## <a name="syntax"></a>语法

```
class CUIntArray : public CObject
```

## <a name="members"></a>成员

成员函数`CUIntArray`类似于类的成员函数[CObArray](../../mfc/reference/cobarray-class.md)。 由于此相似性，因此你可以使用 `CObArray` 参考文档获取成员函数细节。 无论您在何处`CObject`作为函数参数或返回值的指针替换 UINT。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，转换为

`UINT CUIntArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|构造一个空数组。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|向数组的末尾添加一个元素；根据需要扩展该数组。|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|将另一个数组追加到该数组中；根据需要扩展该数组。|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|将另一个数组复制到该数组；根据需要扩展该数组。|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|在该数组中返回对元素指针的临时引用。|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|若高于当前的上限，则将释放所有未使用的内存。|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|返回给定索引位置处的值。|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|获取此数组中的元素数。|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|允许访问该数组中的元素。 可以为 NULL。|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|获取此数组中的元素数。|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|返回最大的有效索引。|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|在指定索引处插入一个元素（或另一个数组中的所有元素）。|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|确定数组是否为空。|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|从此数组中移除所有元素。|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引处的元素。|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|设置给定索引的值；不允许对该数组进行扩展。|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|设置给定索引的值；根据需要扩展该数组。|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|设置要在该数组中包含的元素数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CObArray::operator]](../../mfc/reference/cobarray-class.md#operator_at)|设置或获取位于指定索引处的元素。|

## <a name="remarks"></a>备注

无符号的整数或 UINT，不同于单词和双字数组，具体取决于操作环境的目标可以更改 UINT 的物理大小。 UINT 是双字具有相同的大小。

`CUIntArray` 合并[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)宏来支持运行时类型访问和转储到[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象。 如果需要单个无符号的整数的元素的转储，你必须将转储上下文的深度设置为 1 或更高版本。 无符号的整数数组无法序列化。

> [!NOTE]
>  在使用数组之前，先使用 `SetSize` 建立其大小并为其分配内存。 如果不使用 `SetSize`，则向数组添加元素会导致它经常重新分配和复制。 经常重新分配和复制会降低效率而且会产生内存碎片。

有关使用的详细信息`CUIntArray`，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CUIntArray`

## <a name="requirements"></a>要求

**标头：** afxcoll.h

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)

