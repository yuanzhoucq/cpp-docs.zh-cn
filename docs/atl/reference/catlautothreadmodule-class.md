---
title: CAtlAutoThreadModule 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b534190a4e7243f5192e6d703b056d8bcb327ca
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110638"
---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule 类

此类实现为在线程池的单元模型 COM 服务器。

> [!IMPORTANT]
> 不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>备注

`CAtlAutoThreadModule` 派生自[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)并实现为在线程池的单元模型 COM 服务器。 `CAtlAutoThreadModule` 使用[CComApartment](../../atl/reference/ccomapartment-class.md)管理模块中的每个线程单元。

必须使用[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)中指定的对象的类定义的宏[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)用作类工厂。 然后，您应该添加派生自的类的单一实例`CAtlAutoThreadModuleT`如`CAtlAutoThreadModule`。 例如：

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> 此类替换已过时[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>要求

**标头：** atlbase.h

## <a name="see-also"></a>请参阅

[CAtlAutoThreadModuleT 类](../../atl/reference/catlautothreadmodulet-class.md)   
[IAtlAutoThreadModule 类](../../atl/reference/iatlautothreadmodule-class.md)   
[类概述](../../atl/atl-class-overview.md)   
[Module 类](../../atl/atl-module-classes.md)
