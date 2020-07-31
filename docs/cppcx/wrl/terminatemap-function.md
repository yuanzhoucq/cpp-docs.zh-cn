---
title: TerminateMap 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 2aa4d6733d2a4e458ff8abff192778d52a4522b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233491"
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

*模块*<br/>
[模块](module-class.md)。

*服务器*<br/>
由 parameter *module*指定的模块中的类工厂子集的名称。

*forceTerminate*<br/>
**`true`** 不管类工厂是否处于活动状态，都要终止类工厂;**`false`** 如果任何工厂处于活动状态，则不终止类工厂。

## <a name="return-value"></a>返回值

**`true`** 如果所有类工厂均已终止，则为;否则为 **`false`** 。

## <a name="remarks"></a>备注

关闭指定模块中的类工厂。

## <a name="requirements"></a>要求

**标头：** 模块。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另请参阅

[Microsoft：： WRL：:D etails 命名空间](microsoft-wrl-details-namespace.md)
