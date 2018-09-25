---
title: 对象的一阶段和两阶段构建 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6454e34830591eccb2b696948d02f74ad8cebfd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426570"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>对象的一阶段和两阶段构建

您可以选择两种技术可用于创建图形对象，如钢笔和画笔：

- *一阶段构造*： 构造并初始化该对象在一个阶段，所有这些都有构造函数中的。

- *两阶段构造*： 构造并初始化该对象在两个单独的阶段。 构造函数创建对象并初始化函数对其进行初始化。

两阶段构造始终是更安全的。 一阶段构造中构造函数可能会引发异常，如果提供不正确的参数或内存分配失败。 尽管您需要检查失败，将通过两阶段构造，避免该问题。 在任一情况下，销毁的对象是相同的过程。

> [!NOTE]
>  这些技术适用于创建任何对象，而不只是图形对象。

## <a name="example-of-both-construction-techniques"></a>这两种构造方法的示例

下面的简短示例演示构造 pen 对象的这两种方法：

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [图形对象](../mfc/graphic-objects.md)

- [将图形对象选入设备上下文](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [设备上下文](../mfc/device-contexts.md)

- [在视图中绘制](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>请参阅

[图形对象](../mfc/graphic-objects.md)

