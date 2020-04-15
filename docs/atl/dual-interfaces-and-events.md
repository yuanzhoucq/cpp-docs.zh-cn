---
title: 双接口和事件
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 4ce5048c25bd55feb0f1eb20fc04ec6bfeead746
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319604"
---
# <a name="dual-interfaces-and-events"></a>双接口和事件

虽然可以将事件接口设计为双接口，但有许多很好的设计理由不这样做。 根本原因是事件的来源将仅通过 vtable 或 通过`Invoke`（）触发事件，而不是两者。 如果事件源将事件触发为直接 vtable 方法调用，则`IDispatch`永远不会使用这些方法，并且接口显然应该是一个纯 vtable 接口。 如果事件源将触发事件作为调用`Invoke`，则永远不会使用 vtable 方法，并且很明显接口应该是一个接口。 如果将事件接口定义为双，则需要客户端实现永远不会使用的接口的一部分。

> [!NOTE]
> 此参数通常不适用于双接口。 从实现的角度来看，双元是一种快速、方便且支持良好的实现接口的方法，这些接口可供各种客户端访问。

还有其他原因可以避免双事件接口;无论是视觉基础还是 Internet 资源管理器都支持它们。

## <a name="see-also"></a>另请参阅

[双接口和 ATL](../atl/dual-interfaces-and-atl.md)
