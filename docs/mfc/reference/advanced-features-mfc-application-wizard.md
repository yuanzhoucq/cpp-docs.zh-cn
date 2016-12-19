---
title: "MFC 应用程序向导的高级功能 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.advanced"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 应用程序向导，高级功能"
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
caps.latest.revision: 17
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 应用程序向导的高级功能
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题列出了应用程序的附加功能选项，如帮助、打印支持等。  在每个部分中，指定这些高级功能的附加支持。  
  
 **上下文相关帮助\(HTML\)**  
 为上下文相关帮助生成一组帮助文件，可以通过使用 F1 和“帮助”菜单或通过单击对话框上的**“帮助”**按钮来查看这些文件。  帮助支持需要帮助编译器。  如果没有帮助编译器，可以通过运行安装程序来安装它。  
  
 请参阅 [HTML 帮助：为程序提供区分上下文的帮助](../../mfc/html-help-context-sensitive-help-for-your-programs.md)和[帮助文件（HTML 帮助）](../../ide/help-files-html-help.md)获取详细信息。  
  
 **打印和打印预览**  
 通过从 MFC 库调用 [CView Class](../../mfc/reference/cview-class.md)中的成员函数，生成用于处理打印、打印设置和打印预览命令的代码。  该向导也会向应用程序的菜单添加这些函数的命令。  打印支持仅适用于在该向导的[MFC 应用程序向导的应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)页中指定**“文档\/视图体系结构支持”**的应用程序。  默认情况下，文档\/视图应用程序具有打印支持。  
  
 **自动化**  
 指定应用程序可以处理在另一个应用程序中实现的对象，或者向自动化客户端公开应用程序。  
  
 **ActiveX 控件**  
 支持 ActiveX 控件（默认值）。  如果不选中此选项且稍后希望在项目中插入 ActiveX 控件，则必须在应用程序的 [CWinApp::InitInstance](../Topic/CWinApp::InitInstance.md) 成员函数中添加对 [AfxEnableControlContainer](../Topic/AfxEnableControlContainer.md) 的调用。  
  
 **MAPI \(消息传递 API\)**  
 指定应用程序可以创建、操作、传输和存储邮件。  
  
 **Windows 套接字**  
 支持 Windows 套接字，可以使用这些套接字编写通过 TCP\/IP 网络进行通信的应用程序。  
  
 **Active Accessibility**  
 将对 [IAccessible](http://msdn.microsoft.com/library/windows/desktop/dd318466) 的支持添加到 [CWnd](../../mfc/reference/cwnd-class.md)派生类中，你可以使用它自定义用户界面以便与具有辅助功能的客户端进行更好的交互。  
  
 **公共控件清单**  
 默认情况下启用。  生成应用程序清单以启用 Microsoft Windows XP 或更新版本操作系统附带的公共控件 DLL。  
  
 第 6 版公共控件 DLL 不自动更新现有应用程序所使用的早期版本的公共控件。  若要使用第 6 版公共控件 DLL，你必须创建一个指示应用程序加载 DLL 的应用程序清单。  此公共控件 DLL 还支持 Windows XP 主题。  
  
 应用程序清单还可指定应用程序需要的其他 DLL 和版本。  有关应用程序清单的详细信息，请参阅 [独立应用程序和并行程序集](http://msdn.microsoft.com/library/dd408052) 中的[!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)]。  
  
 **支持重新启动管理器**  
 添加对 [Windows 重新启动管理器](http://msdn.microsoft.com/library/windows/desktop/aa373680\(v=vs.85\).aspx)的支持。  此视频演示如何从 MFC 使用重新启动管理器：[如何：使用新建重新启动管理器](http://msdn.microsoft.com/vstudio/ee886407)。  
  
 **高级框架窗格**  
 |选项|描述|  
|--------|--------|  
|**资源管理器停靠窗格**|在主框架窗口的左侧创建一个类似于 Visual Studio**“解决方案资源管理器”**的停靠窗格。|  
|**输出停靠框架**|在主框架窗口的下方创建一个类似于 Visual Studio**“输出”**窗格的停靠窗格。|  
|**属性停靠窗格**|在主框架窗口的右侧创建一个类似于 Visual Studio**“属性”**窗格的停靠窗格。|  
|**导航窗格**|在主框架窗口的左侧创建一个类似于 Outlook 导航栏的停靠窗格。|  
|**标题栏**|在主框架窗口的上方创建一个 Office 样式的标题栏。|  
  
 **最近文件列表上的文件数**  
 指定要在最近使用的列表中列出的文件数。  默认数是 4。  
  
## 请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)