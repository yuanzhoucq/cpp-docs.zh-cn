---
title: TerminateMap 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: efee7edfc1085288b3220698024cb0deeb4e71af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643217"
---
# <a name="terminatemap-function"></a>TerminateMap 函数

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>参数

*module*<br/>
一个[模块](../windows/module-class.md)。

*服务器名称*<br/>
参数指定的模块中的类工厂的子集名称*模块*。

*forceTerminate*<br/>
**true**终止类而不考虑它们的工厂处于活动状态;**false**不终止类工厂，如果任何工厂处于活动状态。

## <a name="return-value"></a>返回值

**true**如果所有类工厂都已终止; 否则为**false**。

## <a name="remarks"></a>备注

关闭指定的模块中的类工厂。

## <a name="requirements"></a>要求

**标头：** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)