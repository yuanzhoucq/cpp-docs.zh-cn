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
ms.openlocfilehash: 2efe095a6d5b71321cbbe56fdee662509baa4573
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619024"
---
# <a name="common-dialog-classes"></a>通用对话框类

除了[CDialog](reference/cdialog-class.md)类之外，MFC 还提供多个派生自 `CDialog` 的类，这些类可封装常用对话框，如下表所示。 封装的对话框称为 "通用对话框"，是 Windows 通用对话框库（COMMDLG）的一部分。DLL）。 在 windows 版本3.1 和更高版本中，Windows 通用对话框中提供了这些类的对话框模板资源和代码。

### <a name="common-dialog-classes"></a>通用对话框类

|派生对话框类|目的|
|--------------------------|-------------|
|[CColorDialog](reference/ccolordialog-class.md)|允许用户选择颜色。|
|[CFileDialog](reference/cfiledialog-class.md)|允许用户选择要打开的文件名或保存。|
|[CFindReplaceDialog](reference/cfindreplacedialog-class.md)|允许用户在文本文件中启动查找或替换操作。|
|[CFontDialog](reference/cfontdialog-class.md)|允许用户指定字体。|
|[CPrintDialog](reference/cprintdialog-class.md)|允许用户为打印作业指定信息。|
|[CPrintDialogEx](reference/cprintdialogex-class.md)|Windows 打印属性表。|

有关常见对话框类的详细信息，请参阅*MFC 参考*中的各个类名称。 MFC 还提供了许多用于 OLE 的标准对话框类。 有关这些类的信息，请参阅*MFC 参考*中的[COleDialog](reference/coledialog-class.md)基类。

MFC 中的其他三个类都具有类似于对话框的特征。 有关[CFormView](reference/cformview-class.md)、 [CRecordView](reference/crecordview-class.md)和[CDaoRecordView](reference/cdaorecordview-class.md)类的信息，请参阅*MFC 参考*中的类。 有关[CDialogBar](reference/cdialogbar-class.md)类的信息，请参阅[对话栏](dialog-bars.md)。

## <a name="see-also"></a>另请参阅

[对话框](dialog-boxes.md)<br/>
[在 MFC 中使用对话框](life-cycle-of-a-dialog-box.md)<br/>
[OLE 中的对话框](dialog-boxes-in-ole.md)
