---
title: 'Event:: event 构造函数 （Windows 运行时 c + + 模板库） |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
dev_langs:
- C++
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bd9f02935d0d88976fd3b62c7276f106519fa74
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381005"
---
# <a name="eventevent-constructor-windows-runtime-c-template-library"></a>Event::Event 构造函数（Windows 运行时 C++ 模板库）

初始化的新实例**事件**类。

## <a name="syntax"></a>语法

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>参数

*h*<br/>
事件的句柄。 默认情况下*h*初始化为**nullptr**。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Event 类（Windows 运行时 C++ 模板库）](../windows/event-class-windows-runtime-cpp-template-library.md)