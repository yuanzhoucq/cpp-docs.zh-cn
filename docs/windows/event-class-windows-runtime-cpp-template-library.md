---
title: Event 类 （Windows 运行时 c + + 模板库） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
dev_langs:
- C++
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c07d58f244bf2e7e6c9329196bae7b5bb323ce12
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644159"
---
# <a name="event-class-windows-runtime-c-template-library"></a>Event 类（Windows 运行时 C++ 模板库）
表示一个事件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
class Event : public HandleT<HandleTraits::EventTraits>;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Event::Event 构造函数（Windows 运行时 C++ 模板库）](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|初始化的新实例**事件**类。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[Event::operator= 运算符](../windows/event-operator-assign-operator.md)|指定将分配**事件**对当前引用**事件**实例。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `HandleT`  
  
 `Event`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)