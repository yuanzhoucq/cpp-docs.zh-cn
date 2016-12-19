---
title: "Grouping Radio Buttons on a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.dialog.grouping"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "member variables, adding to radio button groups"
  - "variables, dialog box control member variables"
  - "dialog box controls, grouping radio buttons"
  - "grouping controls"
  - "radio buttons, grouping on dialog boxes"
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Grouping Radio Buttons on a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当向对话框添加单选按钮时，对于组中的第一个按钮，可通过在属性窗口中设置组属性将它们视为组。 然后该单选按钮的控件 ID 出现在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，让你可以添加单选按钮组的成员变量。  
  
 一个对话框中可以有多组单选按钮，每个组都应使用以下过程添加。  
  
### 向对话框添加一组单选按钮  
  
1.  在“工具箱窗口”[](../Topic/Toolbox.md)中选择单选按钮控件，然后单击要将控件放置到对话框中的位置。  
  
2.  重复执行第一步以根据需要添加多个单选按钮。 请确保组中的单选按钮是按照 Tab 键顺序连续排列的（有关详细信息，请参阅[更改控件的 Tab 键顺序](../mfc/changing-the-tab-order-of-controls.md)）。  
  
3.  在[属性窗口](../Topic/Properties%20Window.md)中，请将按照 Tab 键顺序排列的第一个单选按钮的**组**属性设置为 **True**。  
  
     将**组**属性更改为 **True** 可将 WS\_GROUP 样式添加到资源脚本的对话框对象的按钮条目中，并确保用户一次只能选择按钮组中的一个单选按钮（当用户单击一个单选按钮时，组中其他按钮都被清除）。  
  
    > [!NOTE]
    >  只有组中第一个单选按钮的**组**属性应设置为 **True**。 如果其他控件不是按钮组的一部分，请将组外第一个控件的**组**属性设置为 **True**。 通过按 CTRL\+D 即可查看 Tab 键顺序，快速确定组外的第一个控件。  
  
### 添加单选按钮组的成员变量  
  
1.  按 Tab 键顺序右键单击第一个单选按钮控件（主导控件和**组**属性设置为 True 的控件）。  
  
2.  从快捷菜单中选择“添加变量”。  
  
3.  在[添加成员变量向导](../ide/add-member-variable-wizard.md)中，选择“控制变量”复选框，然后选择“值”单选按钮。  
  
4.  在“变量名称”框中键入新成员变量的名称。  
  
5.  在“变量类型”列表框中，选择“int”或键入“int”。  
  
6.  现在可以通过修改代码来指定哪个单选按钮为选中状态。 例如，m\_radioBox1 \= 0；选中组中第一个单选按钮。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Arrangement of Controls on Dialog Boxes](../mfc/arrangement-of-controls-on-dialog-boxes.md)   
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)