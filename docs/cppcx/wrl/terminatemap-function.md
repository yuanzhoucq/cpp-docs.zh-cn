---
title: TerminateMap 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 2a451bf68bfb543ee5e82a9a48097cac7e8a9821
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026638"
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

*name*<br/>
一个[模块](module-class.md)。

*serverName*<br/>
参数指定的模块中的类工厂的子集名称*模块*。

*forceTerminate*<br/>
**true**终止类而不考虑它们的工厂处于活动状态;**false**不终止类工厂，如果任何工厂处于活动状态。

## <a name="return-value"></a>返回值

**true**如果所有类工厂都已终止; 否则为**false**。

## <a name="remarks"></a>备注

关闭指定的模块中的类工厂。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)