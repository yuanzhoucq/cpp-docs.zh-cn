---
title: IConvertTypeImpl 类
ms.date: 11/04/2016
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
ms.openlocfilehash: e3b76be2a1f1edfcdc1139a3dd396835923c2b4a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210686"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl 类

提供[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))接口的实现。

## <a name="syntax"></a>语法

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IConvertTypeImpl`的类。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[CanConvert](#canconvert)|提供有关命令或行集上类型转换的可用性的信息。|

## <a name="remarks"></a>备注

此接口对命令行集和索引行集是必需的。 `IConvertTypeImpl` 通过委托到 OLE DB 提供的转换对象来实现接口。

## <a name="iconverttypeimplcanconvert"></a><a name="canconvert"></a>IConvertTypeImpl：： CanConvert

提供有关命令或行集上类型转换的可用性的信息。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IConvertType：： CanConvert](/previous-versions/windows/desktop/ms711224(v=vs.85)) 。

### <a name="remarks"></a>备注

使用 `MSADC.DLL`中 OLE DB 数据转换。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
