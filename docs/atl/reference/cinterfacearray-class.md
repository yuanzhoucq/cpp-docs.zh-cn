---
title: CInterfaceArray 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64b6266ac31e2d6dec6eabc847b67b080b250837
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751418"
---
# <a name="cinterfacearray-class"></a>CInterfaceArray 类

构造的 COM 接口指针的数组时，此类提供了有用的方法。

## <a name="syntax"></a>语法

```
template <class I, const IID* piid=& __uuidof(I)>  
class CInterfaceArray : 
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>参数

*I*  
指定要存储的指针的类型的 COM 接口。

*piid*  
指向 IID*我*。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|接口数组构造函数。|

## <a name="remarks"></a>备注

此类提供一个构造函数和创建的 COM 接口指针的数组的派生的方法。 使用[CInterfaceList](../../atl/reference/cinterfacelist-class.md)列表在需要时。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray

构造函数。

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>备注

初始化智能指针数组。

## <a name="see-also"></a>请参阅

[CAtlArray 类](../../atl/reference/catlarray-class.md)   
[CComQIPtr 类](../../atl/reference/ccomqiptr-class.md)   
[CComQIPtrElementTraits 类](../../atl/reference/ccomqiptrelementtraits-class.md)   
[类概述](../../atl/atl-class-overview.md)
