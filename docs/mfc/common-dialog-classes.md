---
title: "通用对话框类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通用对话框 [C++]"
  - "通用对话框 [C++], 通用对话框类"
  - "通用对话框类 [C++]"
  - "对话框 [C++], Windows 通用对话框"
  - "对话框类 [C++]"
  - "对话框类 [C++], 通用"
  - "MFC 对话框, Windows 通用对话框"
  - "Windows 通用对话框 [C++]"
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 通用对话框类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

In addition to class [CDialog](../mfc/reference/cdialog-class.md), MFC supplies several classes derived from `CDialog` that encapsulate commonly used dialog boxes, as shown in the following table.  密封调用对话框“通用对话框”并为 Windows 公共对话框库 \(COMMDLG.DLL\) 的一部分。  对话框模板资源并针对这些类中是 Windows 3.1 版本一部分和后的窗口提供通用对话框。  
  
### 通用对话框类  
  
|派生的对话框类|用途|  
|-------------|--------|  
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|允许用户选择的颜色。|  
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|让用户选择文件名打开或保存。|  
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|允许用户开始查找或替换文本在文件的操作。|  
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|允许用户指定字体。|  
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|让用户与打印作业指定信息。|  
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Windows 2000 的属性表。|  
  
 有关通用对话框类的更多信息，请参见 *MFC 参考* 类名。  MFC 还提供用于 OLE 的许多标准对话框类。  有关这些类的信息，请参见类的基，[COleDialog](../mfc/reference/coledialog-class.md)，" *MFC 参考*。  
  
 MFC 中的其他三个类具有类似于对话框的特性。  有关类的信息，请参见 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)[CFormView](../mfc/reference/cformview-class.md)，[CRecordView](../mfc/reference/crecordview-class.md)和" *MFC 参考"中的*类。  有关类的信息，请参见 [对话栏](../mfc/dialog-bars.md)。[CDialogBar](../mfc/reference/cdialogbar-class.md)  
  
## 请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE 中的对话框](../mfc/dialog-boxes-in-ole.md)