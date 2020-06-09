---
title: 创建并显示对话框
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
ms.openlocfilehash: 649d64f8e8b894027b9d6850b62d357d79c1dafa
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616276"
---
# <a name="creating-and-displaying-dialog-boxes"></a>创建并显示对话框

创建对话框对象是一个两阶段操作。 首先，构造对话框对象，然后创建对话框窗口。 模式和无模式对话框的创建和显示过程有一些不同。 下表列出了正常构造和显示模式和无模式对话框的方式。

### <a name="dialog-creation"></a>对话框创建

|对话类型|如何创建|
|-----------------|----------------------|
|[模态](creating-modeless-dialog-boxes.md)|构造 `CDialog`，然后调用 `Create` 成员函数。|
|[模型](creating-modal-dialog-boxes.md)|构造 `CDialog`，然后调用 `DoModal` 成员函数。|

如果需要，可以从已构造的[内存中对话框模板](using-a-dialog-template-in-memory.md)而不是从对话框模板资源创建对话框。 但这是一个高级主题。

## <a name="see-also"></a>另请参阅

[在 MFC 中使用对话框](life-cycle-of-a-dialog-box.md)
