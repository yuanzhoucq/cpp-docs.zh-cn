---
title: 双重接口和事件
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 01233edb63145d69d335349bb9dff91e6a4aca5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198260"
---
# <a name="dual-interfaces-and-events"></a>双重接口和事件

虽然设计为双重事件接口，但有多种良好的设计原因而无法执行此操作。 基本的原因是事件源将仅触发事件通过 vtable 或`Invoke`，而不是两者。 如果事件源触发该事件作为直接 vtable 方法调用，`IDispatch`永远不会使用方法和很明显接口应该是纯 vtable 接口。 如果事件源触发的事件与调用`Invoke`vtable 方法将永远不使用，它是清除接口应该是调度接口。 如果您定义您的事件接口为双重接口，就要求客户端实现将永远不使用的接口的一部分。

> [!NOTE]
>  此参数不适用于双重接口，一般情况下。 从实现的角度看，双重接口是实现范围广泛的客户端可以访问的接口的快速、 方便，且广受支持的方式。

更多原因，若要避免双事件接口;Visual Basic 和 Internet 资源管理器都不支持它们。

## <a name="see-also"></a>请参阅

[双重接口和 ATL](../atl/dual-interfaces-and-atl.md)
