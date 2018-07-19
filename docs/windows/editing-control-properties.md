---
title: 编辑控件属性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls, editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f7976f74e9454b023c4da51168fa780ccaea2342
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873480"
---
# <a name="editing-control-properties"></a>编辑控件属性
### <a name="to-edit-the-properties-of-a-control-or-controls"></a>若要编辑的控件或控件属性  
  
1.  在对话框中，选择你想要修改的控件。  
  
    > [!NOTE]
    >  如果你选择多个控件，可以编辑仅对所选控件通用的属性。  
  
2.  在[属性窗口](/visualstudio/ide/reference/properties-window)，更改你的控件的属性。  
  
    > [!NOTE]
    >  当你将设置**位图**按钮、 单选按钮或复选框控件等于属性**True**，BS_BITMAP 实现为您的控件的样式。 有关详细信息，请参阅[按钮样式](../mfc/reference/styles-used-by-mfc.md#button-styles)。 将位图与控件关联的示例，请参阅[CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap)。 在对话框的资源编辑器时，位图不会出现在控件上。  
  
### <a name="to-undo-changes-to-the-properties-of-a-control"></a>若要撤消对控件的属性更改  
  
1.  请确保在控件有焦点在对话框编辑器中。  
  
2.  选择**撤消**从**编辑**菜单 (如果焦点在控件上，而不是**撤消**命令都将不可用)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅 [演练：本地化 Windows 窗体](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) 和 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 要求  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [对话框中的控件](../windows/controls-in-dialog-boxes.md)

