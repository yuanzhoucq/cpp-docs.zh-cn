---
title: CAutoPtrArray 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d83f98de4f1d07fbebdd07186729453d2ef1d3b2
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108717"
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray 类

构造的智能指针的数组时，此类提供了有用的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>参数

*E*<br/>
指针类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|构造函数。|

## <a name="remarks"></a>备注

此类提供构造函数，并派生方法从[CAtlArray](../../atl/reference/catlarray-class.md)并[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)来帮助存储智能指针集合类对象的创建。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="cautoptrarray"></a>  CAutoPtrArray::CAutoPtrArray

构造函数。

```
CAutoPtrArray() throw();
```

### <a name="remarks"></a>备注

初始化智能指针数组。

## <a name="see-also"></a>请参阅

[CAtlArray 类](../../atl/reference/catlarray-class.md)   
[CAutoPtrElementTraits 类](../../atl/reference/cautoptrelementtraits-class.md)   
[CAutoPtrList 类](../../atl/reference/cautoptrlist-class.md)   
[类概述](../../atl/atl-class-overview.md)
