---
title: 对对话框中的控件进行类型安全的访问
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- Windows common controls [MFC], in dialog boxes
- safe access to dialog box controls
- dialog boxes [MFC], type-safe access to controls
- controls [MFC], accessing in dialog boxes
- type-safe access to dialog box controls
- MFC dialog boxes [MFC], type-safe access to controls
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
ms.openlocfilehash: 9b8e5aef61d1a7c7277f2a6bd37b81bd156bb837
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181613"
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>对对话框中的控件进行类型安全的访问

对话框中的控件可以使用 MFC 控件类的接口，如 `CListBox` 和 `CEdit`。 您可以创建控件对象并将其附加到对话框控件。 然后，可以通过控件的类接口访问该控件，并调用成员函数以操作该控件。 此处介绍的方法旨在为您提供对控件的类型安全访问。 这对诸如编辑框和列表框之类的控件特别有用。

可通过两种方法在对话框中的控件和 `CDialog` 派生的类中的 C++ 控件成员变量之间建立连接。

- [不使用代码向导](../mfc/type-safe-access-to-controls-without-code-wizards.md)

- [使用代码向导](../mfc/type-safe-access-to-controls-with-code-wizards.md)

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)
