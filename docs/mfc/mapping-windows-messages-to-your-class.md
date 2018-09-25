---
title: Windows 消息映射到您的类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e5c51cfccfa360b7f677ca3a30b7a05e0d4a799
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374452"
---
# <a name="mapping-windows-messages-to-your-class"></a>将 Windows 消息映射到您的类

如果您需要处理 Windows 消息在对话框中，重写相应的处理程序函数。 若要执行此操作，请使用属性窗口[映射消息](../mfc/reference/mapping-messages-to-functions.md)到对话框类。 这将为每个消息的消息映射项，并向类添加消息处理程序成员函数。 使用 Visual c + + 源代码编辑器在消息处理程序中编写代码。

此外可以重写的成员函数[CDialog](../mfc/reference/cdialog-class.md)及其基类，尤其是[CWnd](../mfc/reference/cwnd-class.md)。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [消息处理和映射](../mfc/message-handling-and-mapping.md)

- [经常重写成员函数](../mfc/commonly-overridden-member-functions.md)

- [经常添加的成员函数](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)

