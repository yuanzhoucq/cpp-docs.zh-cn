---
title: CAtlFileMapping 类
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: 58fb08ee48f3cc51a96304b9c1708dbfbf195adb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429713"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping 类

此类表示一个内存映射文件，将强制转换运算符添加到的方法[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>参数

*T*<br/>
使用强制转换运算符的数据类型。

## <a name="members"></a>成员

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAtlFileMapping::operator T *](#operator_t_star)|允许隐式转换`CAtlFileMapping`对象添加到`T*`。|

## <a name="remarks"></a>备注

此类会添加一个单一的强制转换运算符，以允许隐式转换`CAtlFileMapping`对象添加到`T*`。 由基类，提供其他成员[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>要求

**标头：** atlfile.h

##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T *

允许隐式转换`CAtlFileMapping`对象添加到`T*`。

```
operator T*() const throw();
```

### <a name="return-value"></a>返回值

返回`T*`到内存映射文件的起始位置的指针。

### <a name="remarks"></a>备注

调用[CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata)和重新解释为返回的指针`T*`其中*T*是用作模板参数的此类的类型。

## <a name="see-also"></a>请参阅

[CAtlFileMappingBase 类](../../atl/reference/catlfilemappingbase-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
