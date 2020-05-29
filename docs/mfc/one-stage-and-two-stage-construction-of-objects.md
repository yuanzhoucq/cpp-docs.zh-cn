---
title: 对象的一阶段和两阶段构建
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 8f221ac6b63a06c65f932a695dfbf7b93ae7ac96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375972"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>对象的一阶段和两阶段构建

您可以选择两种创建图形对象的技术，如笔和画笔：

- *一阶段构造*：在一个阶段构造和初始化对象，全部使用构造函数。

- *两阶段构造*：分两个阶段构造和初始化对象。 构造函数创建对象，初始化函数将初始化。

两阶段结构始终更安全。 在一阶段构造中，如果提供不正确的参数或内存分配失败，构造函数可能会引发异常。 此问题可以通过两阶段构造避免，尽管您必须检查故障。 在这两种情况下，销毁对象都是相同的过程。

> [!NOTE]
> 这些技术适用于创建任何对象，而不仅仅是图形对象。

## <a name="example-of-both-construction-techniques"></a>两种施工技术示例

下面的简短示例显示了构造笔对象的两种方法：

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [图形对象](../mfc/graphic-objects.md)

- [将图形对象选入设备上下文](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [设备上下文](../mfc/device-contexts.md)

- [视图中的绘图](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>另请参阅

[图形对象](../mfc/graphic-objects.md)
