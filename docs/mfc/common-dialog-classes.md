---
title: 通用对话框类
ms.date: 11/04/2016
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
ms.openlocfilehash: 5efd885421d8c73c191e2a5603f37d1df85a5168
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388522"
---
# <a name="common-dialog-classes"></a>通用对话框类

除了类之外[CDialog](../mfc/reference/cdialog-class.md)，MFC 提供多个类派生自`CDialog`，它封装常用的对话框框中下, 表中所示。 封装的对话框称为"公共对话框"，它们属于 Windows 公共对话框库 (COMMDLG。DLL)。 对话框模板资源和代码，这些类中提供了 Windows 公共对话框是 Windows 3.1 及更高版本的一部分。

### <a name="common-dialog-classes"></a>通用对话框类

|在派生的对话框类|用途|
|--------------------------|-------------|
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|允许用户选择颜色。|
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|允许用户选择打开或保存的文件名。|
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|允许用户开始执行查找或替换操作在文本文件中。|
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|允许用户指定的字体。|
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|允许用户指定打印作业的信息。|
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Windows 打印属性表。|

有关通用对话框类的详细信息，请参阅中的单个类名称*MFC 参考*。 MFC 还提供了大量用于 OLE 的标准对话框类。 有关这些类的信息，请参阅基类[COleDialog](../mfc/reference/coledialog-class.md)，在*MFC 参考*。

MFC 中的其他三个类具有类似于对话框的特征。 有关类信息[CFormView](../mfc/reference/cformview-class.md)， [CRecordView](../mfc/reference/crecordview-class.md)，并[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)，请参阅中的类*MFC 参考*。 有关类信息[CDialogBar](../mfc/reference/cdialogbar-class.md)，请参阅[对话栏](../mfc/dialog-bars.md)。

## <a name="see-also"></a>请参阅

[对话框](../mfc/dialog-boxes.md)<br/>
[对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE 中的对话框](../mfc/dialog-boxes-in-ole.md)
