---
title: CAtlFileMapping 类
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: ca46ccdacf5ea24f1de26cdc75bf808c4ecfaa40
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318962"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping 类

此类表示内存映射文件，将强制转换运算符添加到[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>参数

*T*<br/>
用于强制转换运算符的数据类型。

## <a name="members"></a>成员

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAtlFile映射：：运算符 T*](#operator_t_star)|允许将`CAtlFileMapping`对象隐式转换为`T*`。|

## <a name="remarks"></a>备注

此类添加单个强制转换运算符，以允许`CAtlFileMapping`将对象隐式转换为`T*`。 其他成员由基类[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)提供。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAtlFile映射库](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>要求

**标题：** atlfile.h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFile映射：：运算符 T*

允许将`CAtlFileMapping`对象隐式转换为`T*`。

```
operator T*() const throw();
```

### <a name="return-value"></a>返回值

返回指向`T*`内存映射文件的开头的指针。

### <a name="remarks"></a>备注

调用[CAtlFileMappingBase：getData](../../atl/reference/catlfilemappingbase-class.md#getdata)并将返回的指针重新解释为`T*` *T*是用作此类模板参数的类型的类型。

## <a name="see-also"></a>另请参阅

[CAtlFileMappingBase 类](../../atl/reference/catlfilemappingbase-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
