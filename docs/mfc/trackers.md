---
title: 跟踪器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 414a7c19292e154af0b6365b766d865dca0a7dd3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439857"
---
# <a name="trackers"></a>跟踪器

[CRectTracker](../mfc/reference/crecttracker-class.md)类提供你的应用程序和您的用户通过提供多种显示样式中的矩形项之间的用户界面。 这些样式包括 solid、 阴影，或虚线边框。阴影的图案涵盖项;和可以位于在外部或内部边框的大小调整句柄。 跟踪器通常与 OLE 项的配合使用，即对象派生自`COleClientItem`。 跟踪器矩形为视觉提示提供项的当前状态。

MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)演示使用跟踪器和容器应用程序的 OLE 客户端项从角度来看一个公共接口。 不同的样式的演示和跟踪器对象的功能，请参阅 MFC 常规示例[跟踪器](../visual-cpp-samples.md)。

在 OLE 应用程序中实现跟踪器的详细信息，请参阅[跟踪器： 在 OLE 应用程序中实现跟踪器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>请参阅

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleClientItem 类](../mfc/reference/coleclientitem-class.md)
