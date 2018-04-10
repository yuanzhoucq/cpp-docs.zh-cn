---
title: 高级功能，MFC 应用程序向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.advanced
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c2a9bb9ebb1837dc303e89e04ced496b52d1cdb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="advanced-features-mfc-application-wizard"></a>MFC 应用程序向导的高级功能
本主题列出了应用程序的附加功能选项，如帮助、打印支持等。 在每个部分中，指定这些高级功能的附加支持。  
  
 **上下文相关帮助 (HTML)**  
 生成一组帮助文件的上下文相关帮助，可通过使用 F1 和帮助菜单上，或通过单击**帮助**出现在对话框中的按钮。 帮助支持需要帮助编译器。 如果没有帮助编译器，可以通过运行安装程序来安装它。  
  
 请参阅[HTML 帮助： 程序的上下文相关帮助](../../mfc/html-help-context-sensitive-help-for-your-programs.md)和[帮助文件 （HTML 帮助）](../../ide/help-files-html-help.md)有关详细信息。  
  
 **打印和打印预览**  
 生成用于处理打印、 打印设置和打印预览命令通过调用成员函数中的代码[CView 类](../../mfc/reference/cview-class.md)从 MFC 库。 该向导也会向应用程序的菜单添加这些函数的命令。 仅对指定的应用程序提供了打印支持**文档/视图体系结构支持**中[应用程序类型、 MFC 应用程序向导](../../mfc/reference/application-type-mfc-application-wizard.md)向导页。 默认情况下，文档/视图应用程序具有打印支持。  
  
 **自动化**  
 指定应用程序可以处理在另一个应用程序中实现的对象，或者向自动化客户端公开应用程序。  
  
 **ActiveX 控件**  
 支持 ActiveX 控件（默认值）。 如果你不选择此选项和以后想要向项目中插入 ActiveX 控件，必须添加对的调用[AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer)应用程序中[CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)成员函数。  
  
 **MAPI (消息传递 API)**  
 指定应用程序可以创建、操作、传输和存储邮件。  
  
 **Windows 套接字**  
 支持 Windows 套接字，可以使用这些套接字编写通过 TCP/IP 网络进行通信的应用程序。  
  
 **Active Accessibility**  
 添加了对支持[IAccessible](http://msdn.microsoft.com/library/windows/desktop/dd318466)到[CWnd](../../mfc/reference/cwnd-class.md)-派生类，可以使用自定义与辅助功能客户端更好的交互的用户界面。  
  
 **公共控件清单**  
 默认情况下启用。 生成应用程序清单以启用 Microsoft Windows XP 或更新版本操作系统附带的公共控件 DLL。  
  
 第 6 版公共控件 DLL 不自动更新现有应用程序所使用的早期版本的公共控件。 若要使用第 6 版公共控件 DLL，你必须创建一个指示应用程序加载 DLL 的应用程序清单。 此公共控件 DLL 还支持 Windows XP 主题。  
  
 应用程序清单还可指定应用程序需要的其他 DLL 和版本。 有关应用程序清单的详细信息，请参阅[独立应用程序和通过并行程序集](http://msdn.microsoft.com/library/dd408052)Windows SDK 中。  
  
 **支持重新启动管理器**  
 添加了对支持[Windows 重新启动管理器](http://msdn.microsoft.com/library/windows/desktop/aa373680\(v=vs.85\).aspx)。 此视频演示如何使用 MFC 中重新启动管理器：[如何： 使用新的重新启动管理器](http://msdn.microsoft.com/vstudio/ee886407)。  
  
 **高级的框架窗格**  
 |选项|描述|  
|------------|-----------------|  
|**资源管理器停靠窗格**|创建一个类似于 Visual Studio 的停靠窗格**解决方案资源管理器**主框架窗口的左侧。|  
|**输出停靠框架**|创建一个类似于 Visual Studio 的停靠窗格**输出**位于主框架窗口下的窗格。|  
|**属性停靠窗格**|创建一个类似于 Visual Studio 的停靠窗格**属性**主框架窗口右侧的窗格。|  
|**导航窗格中**|在主框架窗口的左侧创建一个类似于 Outlook 导航栏的停靠窗格。|  
|**标题栏**|在主框架窗口的上方创建一个 Office 样式的标题栏。|  
  
 **近期文件列表上的文件数量**  
 指定要在最近使用的列表中列出的文件数。 默认数是 4。  
  
## <a name="see-also"></a>请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)

