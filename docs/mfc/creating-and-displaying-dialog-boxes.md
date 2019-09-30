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
ms.openlocfilehash: 6d23e4d2c9249ce248eb8092963036f2ba5cacac
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685736"
---
# <a name="creating-and-displaying-dialog-boxes"></a>创建并显示对话框

创建对话框对象是一个两阶段操作。 首先，构造对话框对象，然后创建对话框窗口。 模式和无模式对话框的创建和显示过程有一些不同。 下表列出了正常构造和显示模式和无模式对话框的方式。

### <a name="dialog-creation"></a>对话框创建

|对话框类型|如何创建|
|-----------------|----------------------|
|[模态](../mfc/creating-modeless-dialog-boxes.md)|构造 `CDialog`，然后调用 `Create` 成员函数。|
|[模型](../mfc/creating-modal-dialog-boxes.md)|构造 `CDialog`，然后调用 `DoModal` 成员函数。|

如果需要，可以从已构造的[内存中对话框模板](../mfc/using-a-dialog-template-in-memory.md)而不是从对话框模板资源创建对话框。 但这是一个高级主题。

## <a name="see-also"></a>请参阅

[使用 MFC 中的对话框](../mfc/life-cycle-of-a-dialog-box.md)
