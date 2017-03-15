---
title: "OLE 中的对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "对话框"
  - "对话框, 关于对话框"
  - "对话框, OLE"
  - "插入对象"
  - "MFC 对话框, OLE 对话框"
  - "OLE 对话框"
  - "OLE 对话框, 关于 OLE 对话框"
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OLE 中的对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当用户运行 OLE 启用应用程序时，有时，当应用程序需要来自用户的信息才能执行操作时。  MFC OLE 类提供很多对话框收集所需信息。  此主题列出了 OLE 对话框处理任务和强制性类显示这些对话框。  有关 OLE 使用的对话框和结构的详细信息来自定义它们的行为，请参见 [MFC 参考](../mfc/mfc-desktop-applications.md)。  
  
 *插入对象*  
 此对话框允许用户插入新创建或现有对象组合到文档。  它还允许用户选择显示项作为图标并启用更改命令图标按钮。  当用户从"编辑"菜单中，选择插入对象中显示此对话框。  使用 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) 类显示此对话框。  注意不能将 MDI 应用程序插入到其本身。  容器是\/服务器的应用程序不能插入到其本身，除非它是 SDI 应用程序。  
  
 *Paste Special*  
 当粘贴数据到复合文档时，此对话框允许用户控制要用到的格式。  用户是否可以选择是否数据的格式，嵌入链接数据和显示为图标。  当用户从"编辑"菜单中，选择粘贴特定中显示此对话框。  使用 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) 类显示此对话框。  
  
 *Change Icon*  
 此对话框允许用户选择要显示图标表示链接的或嵌入项。  显示此对话框，当用户从"编辑"菜单中选择或在特定图标更改选择时的粘贴的 Change 图标按钮或转换对话框。  此外，当用户插入打开对话框并选择显示为图标时，请查看它。  使用 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) 类显示此对话框。  
  
 *Convert*  
 此对话框允许用户更改中嵌入或链接项的类型。  例如，在中，如果在嵌入复合文档的一元文件和之后要使用其他应用程序修改嵌入式元文件，可以使用转换对话框。  此对话框可通过单击菜单上的 *项目类型* 对象通常显示，然后在级联菜单上，单击"转换。  使用 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md) 类显示此对话框。  对于示例，将运行 MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md)。  
  
 *编辑链接或更新了链接*  
 编辑链接对话框允许用户更改有关链接对象的源的信息。  更新了链接对话框验证所有链接的项源中当前对话框中，并根据需要显示编辑链接"对话框。  当用户从"编辑"菜单中，选定链接查看编辑链接"对话框。  首先，当打开时，更新了链接对话框通常显示复合文档。  使用 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) 或 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) 类，根据要显示的对话框。  
  
 *不响应服务器忙碌或的服务器*  
 服务器正忙对话框通常显示，当用户尝试激活项时，服务器当前无法处理请求，因为服务器由其他用户或任务正在使用。  实质上，如果服务器不激活请求没有响应的响应服务器显示对话框。  通过这些对话框显示 `COleMessageFilter`，基于 OLE 接口而 **IMessageFilter**的实现，因此，用户可以决定是否尝试激活再次请求。  使用 [COleBusyDialog](../mfc/reference/colebusydialog-class.md) 类显示此对话框。  
  
## 请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE](../mfc/ole-in-mfc.md)