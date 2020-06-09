---
title: 对象的一阶段和两阶段构建
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 07e006d5b326486c54f23990c604a7d2ee0e4c83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625291"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>对象的一阶段和两阶段构建

你可以选择两种方法来创建图形对象，如笔和画笔：

- *一阶段构造*：在一个阶段构造和初始化对象，所有操作都具有构造函数。

- *两阶段构造*：在两个单独的阶段构造和初始化对象。 构造函数创建对象，而初始化函数对该对象进行初始化。

两阶段构造始终更安全。 在单阶段构造中，如果提供的参数不正确或内存分配失败，则构造函数可能引发异常。 尽管你确实需要检查是否有故障，但这两个阶段的构造避免了这一问题。 在这两种情况下，销毁对象的过程是相同的。

> [!NOTE]
> 这些技术适用于创建任何对象，而不只是图形对象。

## <a name="example-of-both-construction-techniques"></a>这两种构造方法的示例

以下简单示例演示了构造 pen 对象的两种方法：

[!code-cpp[NVC_MFCDocViewSDI#6](codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [图形对象](graphic-objects.md)

- [将图形对象选入设备上下文](selecting-a-graphic-object-into-a-device-context.md)

- [设备上下文](device-contexts.md)

- [在视图中绘制](drawing-in-a-view.md)

## <a name="see-also"></a>另请参阅

[图形对象](graphic-objects.md)
