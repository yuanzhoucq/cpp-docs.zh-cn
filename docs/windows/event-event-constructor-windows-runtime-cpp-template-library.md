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
ms.openlocfilehash: a377967ff2fe469f73f993d779b48037d462e6d7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575880"
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

*h*  
事件的句柄。 默认情况下*h*初始化为**nullptr**。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Event 类（Windows 运行时 C++ 模板库）](../windows/event-class-windows-runtime-cpp-template-library.md)