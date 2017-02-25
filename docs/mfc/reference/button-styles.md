---
title: "按钮样式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BS_DEFPUSHBUTTON"
  - "BS_NOTIFY"
  - "BS_MULTILINE"
  - "BS_AUTOCHECKBOX"
  - "BS_3STATE"
  - "BS_BITMAP"
  - "BS_TOP"
  - "BS_PUSHBUTTON"
  - "BS_PUSHLIKE"
  - "BS_AUTO3STATE"
  - "BS_CHECKBOX"
  - "BS_AUTORADIOBUTTON"
  - "BS_RADIOBUTTON"
  - "BS_OWNERDRAW"
  - "BS_LEFT"
  - "BS_USERBUTTON"
  - "BS_RIGHTBUTTON"
  - "BS_RIGHT"
  - "BS_LEFTTEXT"
  - "BS_TEXT"
  - "BS_BOTTOM"
  - "BS_GROUPBOX"
  - "BS_FLAT"
  - "BS_VCENTER"
  - "BS_ICON"
  - "BS_CENTER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BS_3STATE 常量"
  - "BS_AUTO3STATE 常量"
  - "BS_AUTOCHECKBOX 常量"
  - "BS_AUTORADIOBUTTON 常量"
  - "BS_BITMAP 常量"
  - "BS_BOTTOM 常量"
  - "BS_CENTER 常量"
  - "BS_CHECKBOX 常量"
  - "BS_DEFPUSHBUTTON 常量"
  - "BS_FLAT 常量"
  - "BS_GROUPBOX 常量"
  - "BS_ICON 常量"
  - "BS_LEFT 常量"
  - "BS_LEFTTEXT 常量"
  - "BS_MULTILINE 常量"
  - "BS_NOTIFY 常量"
  - "BS_OWNERDRAW 常量"
  - "BS_PUSHBUTTON 常量"
  - "BS_PUSHLIKE 常量"
  - "BS_RADIOBUTTON 常量"
  - "BS_RIGHT 常量"
  - "BS_RIGHTBUTTON 常量"
  - "BS_TEXT 常量"
  - "BS_TOP 常量"
  - "BS_USERBUTTON 常量"
  - "BS_VCENTER 常量"
  - "按钮对象 (CButton), 按钮样式"
  - "样式, 按钮对象"
ms.assetid: 41206f72-2b92-4250-ae32-31184046402f
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# 按钮样式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题描述按钮类型和样式。  
  
## 按钮类型  
 下表列出了按钮类型。  可以选择下列项目之一。  如果不指定按钮类型，则默认为  `BS_PUSHBUTTON`。  
  
|类型|说明|  
|--------|--------|  
|`BS_3STATE`|创建具有三种状态的复选框按钮：`BST_CHECKED`、`BST_INDETERMINATE` 和  `BST_UNCHECKED`。  单击按钮将发送 `BN_CLICKED` 通知到所有者窗口，但并不更改按钮的状态。  默认情况下，关联的文本显示在复选框右侧。  若要在复选框左侧显示文本，请使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 样式。|  
|`BS_AUTO3STATE`|创建具有三种状态的复选框按钮：`BST_CHECKED`、`BST_INDETERMINATE` 和  `BST_UNCHECKED`。  单击按钮将发送 `BN_CLICKED` 通知到所有者窗口并更改按钮的状态。  按钮的状态按 `BST_CHECKED`、`BST_INDETERMINATE` 和  `BST_UNCHECKED` 的顺序循环。  默认情况下，关联的文本显示在复选框右侧。  若要在复选框左侧显示文本，请使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 样式。|  
|`BS_AUTOCHECKBOX`|创建具有两种状态的复选框按钮：`BST_CHECKED` 和 `BST_UNCHECKED`。  单击按钮将发送 `BN_CLICKED` 通知到所有者窗口并更改按钮的状态。  默认情况下，关联的文本显示在复选框右侧。  若要在复选框左侧显示文本，请使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 样式。|  
|`BS_AUTORADIOBUTTON`|创建具有两种状态的单选按钮：`BST_CHECKED` 和 `BST_UNCHECKED`。  单选按钮通常在组中使用，每个组一次最多可以拥有一个选中项。  单击按钮将发送 `BN_CLICKED` 通知到所有者窗口，将选中的单选按钮的状态设置为 `BST_CHECKED`，然后将按钮组中的其他所有单选按钮的状态设置为  `BST_UNCHECKED`。  默认情况下，关联的文本显示在单选按钮右侧。  若要在单选按钮左侧显示文本，请使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 样式。|  
|`BS_CHECKBOX`|创建具有两种状态的复选框按钮：`BST_CHECKED` 和 `BST_UNCHECKED`。  单击按钮将发送 `BN_CLICKED` 通知到所有者窗口，但并不更改按钮的状态。  默认情况下，关联的文本显示在复选框右侧。  若要在复选框左侧显示文本，请使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 样式。|  
|`BS_COMMANDLINK`|创建一个命令链接按钮。  命令链接按钮是 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 特有的命令按钮，主文本左边显示有一个绿色按钮，主文本下方显示注释。  可以使用 [CButton::SetNote](../Topic/CButton::SetNote.md) 设置注释文本。|  
|`BS_DEFCOMMANDLINK`|创建一个命令链接按钮。  命令链接按钮是 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 特有的命令按钮，主文本左边显示有一个绿色按钮，主文本下方显示注释。  可以使用 [CButton::SetNote](../Topic/CButton::SetNote.md) 设置注释文本。  如果按钮出现在对话框中，则即使按钮没有输入焦点，也要按 ENTER 键发送一个 `BN_CLICKED` 通知到该对话框。|  
|`BS_DEFPUSHBUTTON`|创建一个具有深黑色边框的命令按钮。  如果按钮出现在对话框中，则即使按钮没有输入焦点，也要按 ENTER 键发送一个 `BN_CLICKED` 通知到该对话框。|  
|`BS_DEFSPLITBUTTON`|创建拆分按钮。  拆分按钮是包含位于下拉箭头旁的按钮 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 特有的命令按钮。  单击该按钮时，系统会执行默认命令。  单击下拉箭头时，其他命令菜单会显示出来。  如果拆分按钮出现在对话框中，则即使按钮没有输入焦点，也要按 ENTER 键发送一个 `BN_CLICKED` 通知到该对话框|  
|`BS_GROUPBOX`|创建一个可在此分组其他按钮的矩形。  该样式的文本在矩形的左上角显示。|  
|`BS_OWNERDRAW`|创建一个所有者描述的按钮。  当按钮的可视方面已更改时，该框架将调用 `DrawItem` 方法。  当使用 `CBitmapButton` 选件类时，必须设置该样式。|  
|`BS_PUSHBUTTON`|创建一个命令按钮，当用户单击按钮时 `BN_CLICKED` 通知将发送到所有者窗口。|  
|`BS_RADIOBUTTON`|创建具有两种状态的单选按钮：`BST_CHECKED` 和 `BST_UNCHECKED`。  单选按钮通常在组中使用，每个组一次最多可以拥有一个选中项。  单击按钮将发送 `BN_CLICKED` 通知到所有者窗口，但并不自动更改组中任何按钮的状态。  默认情况下，关联的文本显示在单选按钮右侧。  若要在单选按钮左侧显示文本，请使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 样式。|  
|`BS_SPLITBUTTON`|创建拆分按钮。  拆分按钮是包含位于下拉箭头旁的按钮 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 特有的命令按钮。  单击该按钮时，系统会执行默认命令。  单击下拉箭头时，其他命令菜单会显示出来。|  
|`BS_USERBUTTON`|已弃用，但可与 Windows 16 位版兼容。  基于 Win32 的应用程序应改用 `BS_OWNERDRAW`。|  
  
## 单选按钮和复选框样式  
 下表列出了特定于单选按钮和复选框的样式。  其他按钮类型都忽略这些样式。  可以选择以下一个或多个项目。  
  
|样式|说明|  
|--------|--------|  
|`BS_LEFTTEXT`|在单选按钮或复选框样式中，该文本显示在单选按钮或复选框的左侧。|  
|`BS_RIGHTBUTTON`|在单选按钮或复选框样式中，该文本显示在单选按钮或复选框的左侧。  此样式与 `BS_LEFTTEXT` 样式相同。|  
|`BS_PUSHLIKE`|使复选框或单选按钮的外观和行为与命令按钮相似。  当该按钮显示为 `BST_CHECKED` 时处于按下状态，当显示为 `BST_INDETERMINATE` 时处于按下和灰显状态，当显示为 `BST_UNCHECKED` 时处于释放状态。|  
  
## 文本对齐样式  
 下表列出了水平和垂直文本对齐选项。  可以选择下列项目之一。  
  
|样式|说明|  
|--------|--------|  
|`BS_LEFT`|将矩形按钮内的文本左对齐。  但是，如果该按钮是不具有 `BS_RIGHTBUTTON` 样式的复选框或单选按钮，则该文本将在复选框或单选按钮右侧进行左端对齐。|  
|`BS_RIGHT`|将矩形按钮内的文本右对齐。  但是，如果该按钮是不具有 `BS_RIGHTBUTTON` 样式的复选框或单选按钮，则该文本将在复选框或单选按钮右侧进行右端对齐。|  
|`BS_CENTER`|将按钮内的文本水平居中对齐。|  
|`BS_TOP`|将文本置于矩形按钮的顶部。|  
|`BS_BOTTOM`|将文本置于矩形按钮的底部。|  
|`BS_VCENTER`|将按钮内的文本垂直居中对齐。|  
  
## 按钮内容选项  
 下表列出了用于指示按钮中显示的内容的选项。  仅显示文本忽略这些样式的按钮类型。  可以选择下列项目之一。  
  
|样式|说明|  
|--------|--------|  
|`BS_BITMAP`|将按钮指定成以位图形式显示。|  
|`BS_ICON`|指定按钮以图标形式显示。|  
|`BS_TEXT`|将按钮指定成以文本形式显示。|  
  
## 其他选项  
 下表列出了可用于任意按钮类型的附加选项。  可以选择以下一个或多个项目。  
  
|样式|说明|  
|--------|--------|  
|`BS_FLAT`|指定按钮是二维的且不带默认底纹以绘制三维图形。|  
|`BS_MULTILINE`|如果文本字符串太长而无法容纳在该按钮矩形的一行中，那么就将按钮文本折为多行。|  
|`BS_NOTIFY`|启用一个按钮以发送 `BN_DBLCLK`、`BN_KILLFOCUS` 和 `BN_SETFOCUS` 通知消息到其父窗口。  请注意，按钮将发送 `BN_CLICKED` 通知，而无论是否指定样式。|  
  
## 请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [CButton::Create](../Topic/CButton::Create.md)   
 [Button 样式](http://msdn.microsoft.com/library/windows/desktop/bb775951)   
 [BN\_CLICKED Notification](_win32_bn_clicked_notification)