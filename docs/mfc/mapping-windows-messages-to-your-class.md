---
title: 将 Windows 消息映射到您的类
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 0f1207faca56acd709db86478722eba85eeb284a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685606"
---
# <a name="mapping-windows-messages-to-your-class"></a>将 Windows 消息映射到您的类

如果需要对话框来处理 Windows 消息，请重写适当的处理程序函数。 为此，请在**解决方案资源管理器**中选择 "**类视图**" 选项卡，右键单击表示对话框的类，然后选择 "[类向导](reference/mfc-class-wizard.md)"。 使用向导将[消息映射](../mfc/reference/mapping-messages-to-functions.md)到对话框类。 这会为每条消息编写消息映射项，并将消息处理程序成员函数添加到类中。 使用代码编辑器在消息处理程序中编写代码。

还可以重写[CDialog](../mfc/reference/cdialog-class.md)及其基类的成员函数（特别是[CWnd](../mfc/reference/cwnd-class.md)）。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [消息处理和映射](../mfc/message-handling-and-mapping.md)

- [经常重写的成员函数](../mfc/commonly-overridden-member-functions.md)

- [经常添加的成员函数](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[使用 MFC 中的对话框](../mfc/life-cycle-of-a-dialog-box.md)
