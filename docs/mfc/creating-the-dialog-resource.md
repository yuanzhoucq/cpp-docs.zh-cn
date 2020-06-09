---
title: 创建对话框资源
ms.date: 11/04/2016
helpviewer_keywords:
- dialog resources
- MFC dialog boxes [MFC], creating
- dialog templates [MFC], creating dialog resource
- templates [MFC], creating
- resources [MFC], creating dialog boxes
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 0b83bd33-14d3-4611-8129-fccdae18053e
ms.openlocfilehash: efaef11cfdc036a201ced3357ca81b37a5dc29db
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619624"
---
# <a name="creating-the-dialog-resource"></a>创建对话框资源

若要设计[对话框](dialog-boxes.md)并创建对话框资源，请使用[对话框编辑器](../windows/dialog-editor.md)。 在对话框编辑器中，您可以：

- 调整您的对话框在显示时将具有的大小和位置。

- 从控件调色板将各种控件拖至对话框中您希望它们所处的位置。

- 使用工具栏上的对齐按钮确定控件的位置。

- 通过模拟对话框将在你的程序中具有的外观和行为来测试对话框。 在“测试”模式中，您可以通过在文本框中键入文本、单击按键等来操作对话框的控件。

完成后，对话框模板资源将存储在应用程序的资源脚本文件中。 如果需要，之后可以编辑它。 有关如何创建和编辑对话框资源的完整说明，请参阅[对话框编辑器](../windows/dialog-editor.md)主题。 此方法还用于为[CFormView](reference/cformview-class.md)和[CRecordView](reference/crecordview-class.md)类创建对话框模板资源。

当对话框适合你时，请创建一个对话框类并映射其消息，如[使用代码向导创建对话框类](creating-a-dialog-class-with-code-wizards.md)中所述。

## <a name="see-also"></a>另请参阅

[对话框](dialog-boxes.md)<br/>
[在 MFC 中使用对话框](life-cycle-of-a-dialog-box.md)
