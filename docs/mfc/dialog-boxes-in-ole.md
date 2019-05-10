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
ms.openlocfilehash: fa3d87e2cc17e297c3e6387920c6d527d8ddbe39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153406"
---
# <a name="dialog-boxes-in-ole"></a>OLE 中的对话框

在用户运行 OLE 启用应用程序，在应用程序时要执行的操作需来自用户的信息的时间。 MFC OLE 类提供了许多的对话框来收集所需的信息。 本主题列出由 OLE 对话框处理的任务，以及显示这些对话框所需的类。 有关 OLE 对话框和使用自定义其行为的结构的详细信息，请参阅[MFC 参考](../mfc/mfc-desktop-applications.md)。

*插入对象*<br/>
此对话框中为复合文档允许用户将新创建的或现有的对象。 它还允许用户选择以图标形式显示该项，并启用更改图标命令按钮。 显示此对话框中，当用户从编辑菜单中选择插入对象。 使用[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)类，以显示此对话框。 请注意，您无法将 MDI 应用程序插入其本身。 为容器/服务器的应用程序不能插入其本身，除非它是 SDI 应用程序。

*选择性粘贴*<br/>
此对话框，用户可以控制将数据粘贴到复合文档时使用的格式。 用户可以选择的数据格式、 是否嵌入或链接数据，以及是否将其显示为一个图标。 显示此对话框中，当用户从编辑菜单选择选择性粘贴。 使用[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)类，以显示此对话框。

*更改图标*<br/>
此对话框允许用户选择显示哪些图标来表示链接或嵌入项。 在用户从编辑菜单中选择更改图标或选择性粘贴或转换对话框中选择更改图标按钮时显示此对话框。 此外显示它时用户将打开插入对象对话框中，并选择显示为图标。 使用[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)类，以显示此对话框。

*Convert*<br/>
此对话框允许用户更改的嵌入或链接项的类型。 例如，如果您有嵌入复合文档中的图元文件，稍后又想使用另一个应用程序来修改嵌入的图元文件，可以使用转换对话框。 通常通过单击显示此对话框*项类型*对象在编辑菜单上，然后在级联菜单上，单击转换。 使用[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)类，以显示此对话框。 例如，运行 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)。

*编辑链接或更新链接*<br/>
编辑链接对话框允许用户以更改有关链接对象的源的信息。 更新链接对话框验证当前的对话框中的所有链接项的源，并显示编辑链接对话框中，如有必要。 显示编辑链接对话框中，当用户从编辑菜单中选择的链接。 首次打开复合文档时，通常被显示更新链接对话框。 可以使用两种[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)或[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)类中，你想要显示具体取决于哪个对话框。

*服务器忙或服务器未响应*<br/>
当用户尝试激活某项，并且服务器当前无法处理该请求，通常是因为服务器是另一个用户正在使用或任务时，将显示服务器忙对话框。 如果服务器没有在所有响应激活请求，将显示服务器未响应对话框。 通过显示这些对话框`COleMessageFilter`根据 OLE 接口的实现`IMessageFilter`，用户可以决定是否要再次尝试激活请求。 使用[COleBusyDialog](../mfc/reference/colebusydialog-class.md)类，以显示此对话框。

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE](../mfc/ole-in-mfc.md)
