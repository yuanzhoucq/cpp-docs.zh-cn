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
ms.openlocfilehash: e0b7ff31576b345ac2911e62a6e10469845eecba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175025"
---
# <a name="creating-and-displaying-dialog-boxes"></a>创建并显示对话框

创建对话框对象是一个两阶段操作。 首先，构造对话框对象，然后创建对话框窗口。 模式和无模式对话框的创建和显示过程有一些不同。 下表列出了正常构造和显示模式和无模式对话框的方式。

### <a name="dialog-creation"></a>对话框创建

|对话框类型|如何创建|
|-----------------|----------------------|
|[无模式](../mfc/creating-modeless-dialog-boxes.md)|构造 `CDialog`，然后调用 `Create` 成员函数。|
|[Modal](../mfc/creating-modal-dialog-boxes.md)|构造 `CDialog`，然后调用 `DoModal` 成员函数。|

可以如果你想创建对话框[内存中对话框模板](../mfc/using-a-dialog-template-in-memory.md)已构造而不是从对话框模板资源。 但这是一个高级主题。

## <a name="see-also"></a>请参阅

[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)
