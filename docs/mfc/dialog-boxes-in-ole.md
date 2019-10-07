---
title: OLE 中的对话框
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
ms.openlocfilehash: 997bfc0bda05f5a2520c102cb38777b533bcef95
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685786"
---
# <a name="dialog-boxes-in-ole"></a>OLE 中的对话框

当用户运行启用了 OLE 的应用程序时，有时应用程序需要用户提供的信息才能执行该操作。 MFC OLE 类提供多个对话框来收集所需的信息。 本主题列出了 OLE 对话框处理的任务以及显示这些对话框所需的类。 有关 OLE 对话框以及用于自定义其行为的结构的详细信息，请参阅[MFC 参考](../mfc/mfc-desktop-applications.md)。

*插入对象*<br/>
此对话框允许用户将新创建的或现有的对象插入到复合文档中。 它还允许用户选择将项显示为图标，并启用 "更改图标" 命令按钮。 当用户从 "编辑" 菜单中选择 "插入对象" 时，显示此对话框。 使用[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)类可显示此对话框。 请注意，您无法将 MDI 应用程序插入其本身。 为容器/服务器的应用程序不能插入其本身，除非它是 SDI 应用程序。

*选择性粘贴*<br/>
此对话框允许用户控制将数据粘贴到复合文档时所使用的格式。 用户可以选择数据的格式，无论是嵌入数据还是链接数据，以及是否将其显示为图标。 当用户从 "编辑" 菜单中选择 "粘贴特殊" 时，显示此对话框。 使用[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)类可显示此对话框。

*更改图标*<br/>
此对话框允许用户选择显示哪个图标来表示链接项或嵌入项。 当用户从 "编辑" 菜单中选择 "更改" 图标或选择 "粘贴特殊或转换" 对话框中的 "更改图标" 按钮时，将显示此对话框。 当用户打开 "插入对象" 对话框并选择 "显示为图标" 时，还会显示此对话框。 使用[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)类可显示此对话框。

*Convert*<br/>
此对话框允许用户更改嵌入项或链接项的类型。 例如，如果您已在复合文档中嵌入了一个图元文件，后来又想要使用其他应用程序修改嵌入的图元文件，则可以使用 "转换" 对话框。 单击 "编辑" 菜单上的 "*项目类型*" "对象"，然后单击 "层叠" 菜单上的 "转换"，通常会显示此对话框。 使用[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)类可显示此对话框。 例如，运行 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)。

*编辑链接或更新链接*<br/>
使用 "编辑链接" 对话框，用户可以更改有关链接对象的源的信息。 "更新链接" 对话框将验证当前对话框中所有链接项的源，并在必要时显示 "编辑链接" 对话框。 当用户从 "编辑" 菜单中选择链接时，将显示 "编辑链接" 对话框。 首次打开复合文档时，通常会显示 "更新链接" 对话框。 根据要显示的对话框，使用[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)或[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)类。

*服务器繁忙或服务器无响应*<br/>
当用户尝试激活某个项并且该服务器当前无法处理该请求（通常是因为另一个用户或任务正在使用该服务器）时，将显示 "服务器忙" 对话框。 如果服务器根本没有响应激活请求，则会显示 "服务器未响应" 对话框。 这些对话框基于 OLE 接口的实现 `COleMessageFilter` 显示，`IMessageFilter`，用户可以决定是否再次尝试激活请求。 使用[COleBusyDialog](../mfc/reference/colebusydialog-class.md)类可显示此对话框。

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[使用 MFC 中的对话框](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE](../mfc/ole-in-mfc.md)
