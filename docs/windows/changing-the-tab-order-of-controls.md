---
title: "更改控件的 tab 键顺序 |Microsoft 文档"
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
- controls [C++], tab order
- focus, tab order
- tab controls, tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls, tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dca6b1bb894aa2219a0352ba9c359e6f3c5a4677
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-tab-order-of-controls"></a>更改控件的 Tab 键顺序
Tab 键顺序是在其中 TAB 键在输入的焦点从一个控件移到下一个对话框中的顺序。 通常从左到右、 从上到下一个对话框中，将继续进行 tab 键顺序。 每个控件具有**Tabstop**属性，用于确定控件是否接收输入的焦点。  
  
### <a name="to-set-input-focus-for-a-control"></a>若要设置输入的焦点的控件  
  
1.  在[属性窗口](/visualstudio/ide/reference/properties-window)，选择**True**或**False**中**Tabstop**属性。  
  
 即便是那些没有 Tabstop 属性设置为 True 需要是 tab 键顺序的一部分。 这可能很重要，例如，当你[定义访问密钥 （助记键）](../windows/defining-mnemonics-access-keys.md)不具有标题的控件的。 包含相关控件的访问密钥的静态文本的 tab 键顺序中必须紧跟相关的控件。  
  
> [!NOTE]
>  如果对话框包含重叠的控件，则更改 tab 键次序可能更改控件的显示的方式。 控件所产生更高版本的 tab 键顺序将始终显示在它们之前的 tab 键顺序任何重叠控件之上。  
  
#### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>若要在对话框中查看所有控件的当前 tab 键次序  
  
1.  上**格式**菜单上，单击**tab 键顺序**。  
  
 \- 或 -  
  
-   按 CTRL + d。  
  
#### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>若要更改在对话框中的所有控件的 tab 键次序  
  
1.  上**格式**菜单上，单击**tab 键顺序**。  
  
     每个控件的左上角的数字的当前 tab 键顺序显示其位置。  
  
2.  通过单击你希望按照 TAB 键顺序的每个控件设置 tab 键顺序。  
  
3.  按**ENTER**退出**tab 键顺序**模式。  
  
    > [!TIP]
    >  一旦进入 tab 键顺序模式，你可以按 esc 键或 enter 键可禁止更改 tab 键顺序。  
  
#### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>若要更改两个或多个控件的 tab 键次序  
  
1.  从**格式**菜单上，选择**tab 键顺序**。  
  
2.  指定按顺序的更改将开始的位置。 若要执行此操作，请按住**CTRL**密钥，然后单击你想要更改其顺序开始之前的控件。  
  
     例如，如果你想要更改控件 7 到 9 的顺序，按住 ctrl 键，则首先选择控件 6。  
  
    > [!NOTE]
    >  若要将特定控件设置为数字 1 （第一次的 tab 键顺序） 中，双击控件。  
  
3.  释放 CTRL 键，然后单击你希望从该点按照 TAB 键顺序的控件。  
  
4.  按**ENTER**退出**tab 键顺序**模式。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [在对话框中的控件](../windows/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)

