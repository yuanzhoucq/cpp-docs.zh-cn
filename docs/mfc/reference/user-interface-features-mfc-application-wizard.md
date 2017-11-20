---
title: "用户界面功能，MFC 应用程序向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.exe.ui
dev_langs: C++
helpviewer_keywords: MFC Application Wizard, user interface features
ms.assetid: 59e7b829-a665-42eb-be23-3f2a36eb2dad
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 78bc0d034c7f4e3b5c34596ee83de1b68d8d9173
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="user-interface-features-mfc-application-wizard"></a>MFC 应用程序向导的用户界面功能
本主题说明了可用于指定你的应用程序的外观的选项。 用户界面功能可用于你的项目取决于应用程序中指定的类型[应用程序类型、 MFC 应用程序向导](../../mfc/reference/application-type-mfc-application-wizard.md)MFC 应用程序向导页。 例如，如果你创建单文档界面应用程序，则无法添加子框架样式。  
  
 **主框架样式**  
 设置你的应用程序的主窗口框架的功能。  
  
|选项|描述|  
|------------|-----------------|  
|**粗框架**|创建具有大小调整边框的窗口。 默认值。|  
|**最小化框**|在主框架窗口中包括最小化框。 默认值。|  
|**最大化框**|在主框架窗口中包括最大化框。 默认值。|  
|**最小化**|作为一个图标打开主框架窗口。|  
|**最大化**|将打开到显示的完整大小主框架窗口。|  
|**系统菜单**|在主框架窗口中包括系统菜单。 默认值。|  
|**关于框**|包括**有关**该应用程序。 用户可以从应用程序的访问此框**帮助**菜单。 默认情况下，且不可更改，除非你选中**基于对话框**中[应用程序类型、 MFC 应用程序向导](../../mfc/reference/application-type-mfc-application-wizard.md)页。<br /><br /> **请注意**通常情况下，不可用选项指示，向导不适用于选项到项目中，是否选择或清除不可用项的复选框。 在这种情况下，向导始终添加**有关**除非首先是基于对话框指定项目到项目框中，然后再取消选中框。|  
|**初始的状态栏**|将状态栏添加到你的应用程序。 状态栏包含键盘的 CAPS LOCK、 NUM LOCK 和 SCROLL LOCK 键的自动指示器和菜单命令和工具栏按钮将显示的帮助消息行字符串。 单击此选项还将添加菜单命令来显示或隐藏状态栏。 默认情况下，应用程序具有状态栏。 不适用于基于对话框的应用程序类型。|  
|**拆分窗口**|提供拆分栏。 拆分条将拆分应用程序的主视图。 多文档界面 (MDI) 应用程序，MDI 子框架的客户端窗口是拆分窗口中，且在单文档界面 (SDI) 应用程序和多个顶级文档应用程序中，主框架的客户端窗口拆分窗口。 不适用于基于对话框的应用程序类型。|  
  
 **子框架样式**  
 指定在你的应用程序的外观和子框架的初始状态。 子框架样式均用于 MDI 应用程序。  
  
|选项|描述|  
|------------|-----------------|  
|**子最小化框**|指定的子窗口是否具有最小化按钮 （默认情况下启用）。|  
|**子最大化框**|指定的子窗口是否具有最大化按钮 （默认情况下启用）。|  
|**子最大化**|指定子窗口最初是否设置 cs.style 标志来最大化时**WS_MAXIMIZE**中[PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow)成员函数`CChildFrame`。|  
  
 **命令栏 （功能区菜单/工具栏）**  
 指示应用程序包含菜单、 工具栏和/或功能区。 不适用于基于对话框的应用程序。  
  
|选项|描述|  
|------------|-----------------|  
|**使用经典菜单**|指定你的应用程序包含经典、 非可拖动菜单。|  
|**使用传统的停靠工具栏**|将标准 Windows 工具栏添加到你的应用程序。 工具栏包含用于创建新的文档; 的按钮打开和保存文档文件;复制、 粘贴或打印文本; 剪切和进入帮助模式。 启用此选项还将添加菜单命令来显示或隐藏工具栏。|  
|**使用浏览器样式的工具栏**|将 Internet 资源管理器样式工具栏添加到你的应用程序。|  
|**使用菜单栏和工具栏**|指示你的应用程序包含可拖动菜单栏和工具栏。|  
|**用户定义的工具栏和映像**|允许用户自定义工具栏和在运行时工具栏图像。|  
|**个性化的菜单行为**|指定菜单是否包含项打开时的完整列表或它是否包含只有用户最常使用的命令。|  
|**使用功能区**|使用你的应用程序而不是菜单栏或工具栏中的 Office 2007 类似的功能区。|  
  
 **对话框的标题**  
 有关[CDialog 类](../../mfc/reference/cdialog-class.md)-基于应用程序，此标题显示在对话框中的标题栏中。 若要编辑此字段，必须首先选择**基于对话框**选项下**应用程序类型**。 有关详细信息，请参阅[应用程序类型、 MFC 应用程序向导](../../mfc/reference/application-type-mfc-application-wizard.md)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)

