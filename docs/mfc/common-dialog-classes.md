---
title: "通用对话框类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- dialog classes [MFC]
- dialog boxes [MFC], Windows common dialogs
- common dialog boxes [MFC], common dialog classes
- common dialog classes [MFC]
- MFC dialog boxes [MFC], Windows common dialogs
- Windows common dialogs [MFC]
- dialog classes [MFC], common
- common dialog boxes [MFC]
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d76c387c9aa9f53f8503d3606b2b47cdb5c6be6d
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="common-dialog-classes"></a>通用对话框类
除了类[CDialog](../mfc/reference/cdialog-class.md)，MFC 还提供几个类派生自`CDialog`，封装常用的对话框框中下, 表中所示。 封装的对话框称为"通用对话框"，它们属于 Windows 公共对话框库 (COMMDLG。DLL)。 对话框模板资源和代码，这些类中提供了 Windows 属于的 Windows 版本 3.1 和更高版本的通用对话框。  
  
### <a name="common-dialog-classes"></a>通用对话框类  
  
|在派生的对话框类|目标|  
|--------------------------|-------------|  
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|允许用户选择颜色。|  
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|允许用户选择打开或保存的文件名。|  
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|允许用户开始执行查找或替换操作在文本文件中。|  
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|允许用户指定一种字体。|  
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|允许用户指定为打印作业的信息。|  
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Windows 打印属性表。|  
  
 有关通用对话框类的详细信息，请参阅中的单独的类名称*MFC 参考*。 MFC 还提供了多个用于 OLE 的标准对话框类。 有关这些类的信息，请参阅基本类、 [COleDialog](../mfc/reference/coledialog-class.md)中*MFC 参考*。  
  
 MFC 中的其他三个类具有类似于对话框的特征。 有关类信息[CFormView](../mfc/reference/cformview-class.md)， [CRecordView](../mfc/reference/crecordview-class.md)，和[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)，请参阅中的类*MFC 参考*。 有关类信息[CDialogBar](../mfc/reference/cdialogbar-class.md)，请参阅[对话栏](../mfc/dialog-bars.md)。  
  
## <a name="see-also"></a>请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE 中的对话框](../mfc/dialog-boxes-in-ole.md)

