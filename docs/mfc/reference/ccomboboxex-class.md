---
title: "CComboBoxEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComboBoxEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComboBoxEx class"
  - "组合框 [C++], CComboBoxEx class"
  - "common controls [C++], extended combo boxes"
  - "extended combo boxes, CComboBoxEx class"
  - "Internet Explorer 4.0 common controls"
  - "Windows common controls [C++], extended combo boxes"
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CComboBoxEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过提供扩展组合框控件为图像支持列表。  
  
## 语法  
  
```  
class CComboBoxEx : public CComboBox  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComboBoxEx::CComboBoxEx](../Topic/CComboBoxEx::CComboBoxEx.md)|构造 `CComboBoxEx` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComboBoxEx::Create](../Topic/CComboBoxEx::Create.md)|创建组合框并将它附加到 `CComboBoxEx` 对象。|  
|[CComboBoxEx::CreateEx](../Topic/CComboBoxEx::CreateEx.md)|使用指定的Windows扩展的样式来创建组合框并将它附加到 **ComboBoxEx** 对象。|  
|[CComboBoxEx::DeleteItem](../Topic/CComboBoxEx::DeleteItem.md)|从 **ComboBoxEx** 控件移除项。|  
|[CComboBoxEx::GetComboBoxCtrl](../Topic/CComboBoxEx::GetComboBoxCtrl.md)|检索指向子组合框控件。|  
|[CComboBoxEx::GetEditCtrl](../Topic/CComboBoxEx::GetEditCtrl.md)|检索句柄 **ComboBoxEx** 控件的编辑控件部分。|  
|[CComboBoxEx::GetExtendedStyle](../Topic/CComboBoxEx::GetExtendedStyle.md)|检索为 **ComboBoxEx** 控件正在使用的扩展样式。|  
|[CComboBoxEx::GetImageList](../Topic/CComboBoxEx::GetImageList.md)|检索指向图像列表分配给 **ComboBoxEx** 控件。|  
|[CComboBoxEx::GetItem](../Topic/CComboBoxEx::GetItem.md)|检索特定 **ComboBoxEx** 项目的项目信息。|  
|[CComboBoxEx::HasEditChanged](../Topic/CComboBoxEx::HasEditChanged.md)|确定用户是否更改了 **ComboBoxEx** 的内容通过键入编辑控件。|  
|[CComboBoxEx::InsertItem](../Topic/CComboBoxEx::InsertItem.md)|插入一个新项。**ComboBoxEx** 控件。|  
|[CComboBoxEx::SetExtendedStyle](../Topic/CComboBoxEx::SetExtendedStyle.md)|sets扩展了 **ComboBoxEx** 控件中的样式。|  
|[CComboBoxEx::SetImageList](../Topic/CComboBoxEx::SetImageList.md)|设置图像。**ComboBoxEx** 控件的列表。|  
|[CComboBoxEx::SetItem](../Topic/CComboBoxEx::SetItem.md)|设置一个项的属性。**ComboBoxEx** 控件。|  
|[CComboBoxEx::SetWindowTheme](../Topic/CComboBoxEx::SetWindowTheme.md)|设置扩展组合框控件的视觉样式。|  
  
## 备注  
 使用创建组合框控件的 `CComboBoxEx`，则不再需要实现自己的图像绘制代码。  相反，访问图像的使用 `CComboBoxEx` 从图像列表。  
  
## 图像列表支持  
 在标准组合框，组合框的所有者负责绘制图像通过创建组合框为所有者绘制控件。  当您使用 `CComboBoxEx`时，不必设置绘制样式 **CBS\_OWNERDRAWFIXED** 和 **CBS\_HASSTRINGS**，因为它们提示。  否则，必须执行绘制操作编写代码。  `CComboBoxEx` 控件支持每个项目三个的图像:一个选定状态的，一个未选中状态的和一个复盖图像的。  
  
## 样式  
 `CComboBoxEx` 支持样式 **CBS\_SIMPLE**、 **CBS\_DROPDOWN**、 **CBS\_DROPDOWNLIST**和 **WS\_CHILD**。  通过的其他样式，在创建windows时由控件忽略。  在窗口中创建后，可以通过调用 `CComboBoxEx` 成员函数提供其他组合框样式 [SetExtendedStyle](../Topic/CComboBoxEx::SetExtendedStyle.md)。  这些样式，您可以:  
  
-   设置列表中的字符串搜索区分大小写。  
  
-   创建使用反斜杠的组合框控件\(“\/“\)，杠\(“\\ “\)和一个句点\(“。”\)字符作为运行分隔符。  使用键盘快捷键CTRL\+箭头，这允许用户从运行跳转到运行。  
  
-   设置组合框控件可显示或不显示图像。  如果图像未显示，组合框可以移除调整图像的文本缩进。  
  
-   创建一个收缩组合框控件，包括将其大小设置为，因此它包含它的剪辑更广泛的组合框。  
  
 这些样式标志进一步在 [使用CComboBoxEx](../../mfc/using-ccomboboxex.md)所述。  
  
## 项目以及和回调项目属性  
 项目信息，例如项目和图像的索引，缩进值和文本字符串，在Win32 framework [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)中存储，如 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]所述。  框架还包含对应于回调标志的成员。  
  
 有关详细概念，讨论，请参见 [使用CComboBoxEx](../../mfc/using-ccomboboxex.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 `CComboBoxEx`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [MFC示例MFCIE](../../top/visual-cpp-samples.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)