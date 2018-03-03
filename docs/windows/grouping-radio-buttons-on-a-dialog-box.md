---
title: "将出现在对话框中的单选按钮分组 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.dialog.grouping
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls, grouping radio buttons
- grouping controls
- radio buttons, grouping on dialog boxes
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 39d6f8ac03d4b7c75098306b4b2eb85350a9efe9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="grouping-radio-buttons-on-a-dialog-box"></a>将对话框上的单选按钮分组
当向对话框添加单选按钮时，对于组中的第一个按钮，可通过在属性窗口中设置组属性将它们视为组。 然后该单选按钮的控件 ID 出现在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，让你可以添加单选按钮组的成员变量。  
  
 一个对话框中可以有多组单选按钮，每个组都应使用以下过程添加。  
  
### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>向对话框添加一组单选按钮  
  
1.  在[“工具箱窗口”](/visualstudio/ide/reference/toolbox) 中选择单选按钮控件，然后单击要将控件放置到对话框中的位置。  
  
2.  重复执行第一步以根据需要添加多个单选按钮。 请确保组中的单选按钮是按照 Tab 键顺序连续排列的（有关详细信息，请参阅 [更改控件的 Tab 键顺序](../windows/changing-the-tab-order-of-controls.md)）。  
  
3.  在 [属性窗口](/visualstudio/ide/reference/properties-window)中，请将按照 Tab 键顺序排列的第一个单选按钮的 **组** 属性  设置为 **True**。  
  
     将 **组** 属性更改为 **True** 可将 WS_GROUP 样式添加到资源脚本的对话框对象的按钮条目中，并确保用户一次只能选择按钮组中的一个单选按钮（当用户单击一个单选按钮时，组中其他按钮都被清除）。  
  
    > [!NOTE]
    >  只有组中第一个单选按钮的 **组** 属性应设置为 **True**。 如果你的不是按钮组的一部分的其他控件，设置**组**的第一个控件的属性*，则将组外*到**True**以及。 通过按 CTRL+D 即可查看 Tab 键顺序，快速确定组外的第一个控件。  
  
### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>添加单选按钮组的成员变量  
  
1.  按 Tab 键顺序右键单击第一个单选按钮控件（主导控件和 **组** 属性设置为 True 的控件）。  
  
2.  从快捷菜单中选择**“添加变量”**  。  
  
3.  在 [添加成员变量向导](../ide/add-member-variable-wizard.md)中，选择**“控制变量”** 复选框，然后选择**“值”** 单选按钮。  
  
4.  在**“变量名称”** 框中键入新成员变量的名称。  
  
5.  在**变量类型**列表框中，选择**int**或类型**int**。  
  
6.  现在可以通过修改代码来指定哪个单选按钮为选中状态。 例如，m_radioBox1 = 0；选中组中第一个单选按钮。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 惠?  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [在对话框中的控件](../windows/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)

