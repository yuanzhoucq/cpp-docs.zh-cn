---
title: Rich Edit 控件概述
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: b99a5c6faaae4679b6aef67f240febbfb0f596e8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617707"
---
# <a name="overview-of-the-rich-edit-control"></a>Rich Edit 控件概述

> [!IMPORTANT]
> 如果在对话框中使用 rich edit 控件（无论应用程序是 SDI、MDI 还是基于对话框），则必须在对话框显示之前调用[AfxInitRichEdit](reference/application-information-and-management.md#afxinitrichedit)一次。 调用此函数的一个典型位置位于程序的 `InitInstance` 成员函数中。 您无需在每次显示对话框时调用它，仅第一次需要。 如果您使用 `AfxInitRichEdit`，则不必调用 `CRichEditView`。

Rich edit 控件（[CRichEditCtrl](reference/cricheditctrl-class.md)）提供用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。 也就是说，格式文本编辑控件支持更改选定文本的字符或段落特性。 一些字符特性的示例包括粗体、斜体、字体系列和磅值。 段落特性的示例包括对齐、边距和制表位。 但是，提供用户界面由您决定，无论提供工具栏按钮、菜单项还是格式字符对话框。 还有用于查询当前选择的特性的格式文本编辑控件的函数。 使用这些函数可显示特性的当前设置，例如，如果选择具有粗体字符格式设置特性，则在命令 UI 上设置复选标记。

有关字符和段落格式设置的详细信息，请参阅本主题后面的[字符格式设置](character-formatting-in-rich-edit-controls.md)和[段落格式设置](paragraph-formatting-in-rich-edit-controls.md)。

格式文本编辑控件几乎支持用于多个编辑控件的所有操作和通知消息。 因此，已使用编辑控件的应用程序可以轻松地更改为使用格式文本编辑控件。 其他消息和通知使应用程序可访问格式文本编辑控件独特的功能。 有关编辑控件的信息，请参阅[CEdit](reference/cedit-class.md)。

有关通知的详细信息，请参阅本主题后面[的来自丰富编辑控件的通知](notifications-from-a-rich-edit-control.md)。

## <a name="see-also"></a>另请参阅

[使用 CRichEditCtrl](using-cricheditctrl.md)<br/>
[控件](controls-mfc.md)
