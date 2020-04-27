---
title: CAtlFileMapping 类
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: 7516349e4ec54d8cb90fa6ff23b0ded954aa043b
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168119"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping 类

此类表示内存映射文件，并向[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)的方法添加强制转换运算符。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

### <a name="parameters"></a>参数

*T*<br/>
用于转换运算符的数据类型。

## <a name="members"></a>成员

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAtlFileMapping：： operator T *](#operator_t_star)|允许`CAtlFileMapping`对象隐式转换为`T*`。|

## <a name="remarks"></a>备注

此类添加单个强制转换运算符，以允许将`CAtlFileMapping`对象隐式`T*`转换为。 其他成员由基类[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)提供。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>要求

**标头：** atlfile

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping：： operator T *

允许`CAtlFileMapping`对象隐式转换为`T*`。

```cpp
operator T*() const throw();
```

### <a name="return-value"></a>返回值

返回一个`T*`指针，该指针指向内存映射文件的开头。

### <a name="remarks"></a>备注

调用[CAtlFileMappingBase：：：：](../../atl/reference/catlfilemappingbase-class.md#getdata)重新解释，并将返回`T*`的指针作为，其中*T*是用作此类的模板参数的类型。

## <a name="see-also"></a>另请参阅

[CAtlFileMappingBase 类](../../atl/reference/catlfilemappingbase-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
