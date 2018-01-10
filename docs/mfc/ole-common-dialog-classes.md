---
title: "OLE 通用对话框类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.ole
dev_langs: C++
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0617354337e75e2c2431df894c054722349e2306
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ole-common-dialog-classes"></a>OLE 通用对话框类
以下类处理通过实现很多标准 OLE 对话框来处理常见 OLE 任务。 它们还为 OLE 功能提供了一致的用户界面。  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 由框架使用，旨在包含所有 OLE 对话框的常见实现。 用户界面类别中的所有对话框类都派生自此基类。 `COleDialog` 无法直接使用。  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 显示“插入对象”对话框，即用于插入新的 OLE 链接项或嵌入项的标准用户界面。  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 显示“选择性粘贴”对话框，即用于实现“编辑选择性粘贴”命令的标准用户界面。  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 显示“编辑链接”对话框，即用于修改有关链接项的信息的标准用户界面。  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 显示“更改图标”对话框，即用于更改与 OLE 嵌入项或链接项关联的图标的标准用户界面。  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 显示“转换”对话框，即用于将 OLE 项从一种类型转换为另一种类型的标准用户界面。  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 封装“Windows 公共 OLE 属性”对话框。 “公共 OLE 属性”对话框提供了一个简单方法，使您能够采用与 Windows 标准一致的方式来显示和修改 OLE 文档项的属性。  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 显示“更新”对话框，即用于更新文档中的所有链接的标准用户界面。 对话框包含一个进度指示器，用来指示更新过程还有多久完成。  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 显示“更改源”对话框，即用于更改链接的目标或源的标准用户界面。  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 显示“服务器忙”和“服务器不响应”对话框，即用于处理对繁忙的应用程序的调用的标准用户界面。 通常由 `COleMessageFilter` 实现自动显示。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

