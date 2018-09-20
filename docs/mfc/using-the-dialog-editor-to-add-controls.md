---
title: 使用对话框编辑器添加控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controls [MFC], adding to dialog boxes
- Dialog editor, creating controls
- common controls [MFC], adding
ms.assetid: d3f9f994-7e54-4656-a545-42c204557c36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffbfad4025e9daf72a9555ca69a8639cba6d68c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374718"
---
# <a name="using-the-dialog-editor-to-add-controls"></a>使用对话框编辑器添加控件

当创建对话框模板资源与[对话框编辑器](../windows/dialog-editor.md)，从控件调色板拖动控件并将其放入对话框的。 这会对该控件类型的规范添加到对话框模板资源。 当构造对话框对象并调用其`Create`或`DoModal`成员函数，该框架创建 Windows 控件，并将其放在屏幕上的对话框窗口中。

可以改为[手动创建控件](../mfc/adding-controls-by-hand.md)的前提。 这是更多的工作。

## <a name="see-also"></a>请参阅

[创建和使用控件](../mfc/making-and-using-controls.md)<br/>
[控件](../mfc/controls-mfc.md)

