---
title: OLE 中的对话框 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fe7f9b4b97fd17e73c3dd9f113a87d8f087b93c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929658"
---
# <a name="dialog-boxes-in-ole"></a>OLE 中的对话框
在用户运行 OLE 启用应用程序，可以在应用程序时才能执行的操作需要从用户的信息的时间。 MFC OLE 类提供了许多的对话框，以收集所需的信息。 本主题列出由 OLE 对话框的任务和显示这些对话框所需的类。 OLE 对话框和用于自定义其行为的结构的详细信息，请参阅[MFC 参考](../mfc/mfc-desktop-applications.md)。  
  
 *插入对象*  
 此对话框用于用户插入新创建的或现有的对象将转换为复合文档。 它还允许用户选择以图标形式显示的项，并启用更改图标命令按钮。 显示此对话框中，当用户从编辑菜单选择插入对象。 使用[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)类来显示此对话框。 请注意，您无法将 MDI 应用程序插入其本身。 为容器/服务器的应用程序不能插入其本身，除非它是 SDI 应用程序。  
  
 *选择性粘贴*  
 此对话框中，用户可以控制将数据粘贴到复合文档时使用的格式。 用户可以选择的数据格式、 是否嵌入或链接数据，以及是否显示为图标。 显示此对话框中，当用户从编辑菜单选择选择性粘贴。 使用[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)类来显示此对话框。  
  
 *更改图标*  
 此对话框允许用户选择显示的图标表示链接或嵌入项。 在用户从编辑菜单中选择更改图标，或选择性粘贴或转换对话框中选择更改图标按钮时显示此对话框。 此外显示当用户打开插入对象对话框中，并选择显示为图标。 使用[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)类来显示此对话框。  
  
 *将转换*  
 此对话框允许用户更改的嵌入或链接的项的类型。 例如，如果有嵌入复合文档中的图元文件，并且稍后想要使用另一个应用程序来修改嵌入的图元文件，你可以使用转换对话框。 单击通常会显示此对话框*项目类型*对象在编辑菜单上，然后在级联菜单上，单击转换。 使用[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)类来显示此对话框。 例如，运行 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)。  
  
 *编辑链接或更新链接*  
 编辑链接对话框中允许用户以更改有关链接对象的源的信息。 更新链接对话框中验证在当前的对话框中的所有链接项的源，并显示编辑链接对话框中，如有必要。 显示编辑链接对话框中，当用户从编辑菜单中选择的链接。 首次打开复合文档时，通常被显示更新链接对话框。 可以使用两种[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)或[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)类中，具体取决于哪个对话框你想要显示。  
  
 *服务器忙或服务器未响应*  
 当用户尝试激活某个项，并且服务器当前无法处理该请求，通常是由于服务器正在使用另一个用户或任务时，将显示服务器忙对话框。 如果服务器未在所有响应对激活请求，将显示服务器未响应对话框。 显示这些对话框显示通过`COleMessageFilter`根据 OLE 接口的实现， `IMessageFilter`，用户可以决定是否要再次尝试激活请求。 使用[COleBusyDialog](../mfc/reference/colebusydialog-class.md)类来显示此对话框。  
  
## <a name="see-also"></a>请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE](../mfc/ole-in-mfc.md)

