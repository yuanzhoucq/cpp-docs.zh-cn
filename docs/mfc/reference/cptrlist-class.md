---
title: CPtrList 类
ms.date: 11/04/2016
f1_keywords:
- CPtrList
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
ms.openlocfilehash: d7da4fe52d25d9ffdf6371aa40f41d7082f1165c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226836"
---
# <a name="cptrlist-class"></a>CPtrList 类

支持 void 指针列表。

## <a name="syntax"></a>语法

```
class CPtrList : public CObject
```

## <a name="members"></a>成员

的成员函数 `CPtrList` 类似于类[CObList](../../mfc/reference/coblist-class.md)的成员函数。 由于此相似性，因此你可以使用 `CObList` 参考文档获取成员函数细节。 无论你在何处看到 `CObject` 作为函数参数或返回值的指针，都要将指针替换为 **`void`** 。

`CObject*& CObList::GetHead() const;`

例如，转换为

`void*& CPtrList::GetHead() const;`

## <a name="remarks"></a>备注

`CPtrList`合并了 IMPLEMENT_DYNAMIC 宏，以支持运行时类型访问和转储到 `CDumpContext` 对象。 如果需要单个指针列表元素的转储，则您必须将转储上下文的深度设为 1 或更大的值。

无法对指针列表进行序列化。

当删除 `CPtrList` 对象或其元素时，仅删除指针而不是指针引用的实体。

有关使用的详细信息 `CPtrList` ，请参阅文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CPtrList`

## <a name="requirements"></a>要求

**标头：** afxcoll。h

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CObList 类](../../mfc/reference/coblist-class.md)
