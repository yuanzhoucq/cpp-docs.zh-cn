---
title: InvokeModeOptions 结构
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 9bca49479d97ee371f6728f90a9aa96da0387f54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213832"
---
# <a name="invokemodeoptions-structure"></a>InvokeModeOptions 结构

指定是激发委托队列中的所有事件，还是在引发错误后停止激发。 允许的值是在 `InvokeMode` 枚举中指定的。

## <a name="syntax"></a>语法

```cpp
enum InvokeMode
{
   StopOnFirstError = 1,
   FireAll = 2,
};

struct InvokeModeOptions
{
   static const InvokeMode invokeMode = invokeModeValue;
};
```

## <a name="requirements"></a>要求

**标头：** 事件。h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)<br/>
[Microsoft：： WRL：： AgileEventSource 类](agileeventsource-class.md)
