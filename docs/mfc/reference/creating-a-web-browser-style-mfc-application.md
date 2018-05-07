---
title: 创建 Web 浏览器样式的 MFC 应用程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcweb.project
dev_langs:
- C++
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20c7228b08200466bd62d1cdbbf7e2f66f8efebb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-web-browser-style-mfc-application"></a>创建 Web 浏览器样式的 MFC 应用程序
Web 浏览器样式的应用程序可以在本地文件系统中和网络上从 （如 HTML 或活动文档） Internet 或 intranet，以及文件夹访问信息。 通过派生从应用程序的视图类[CHtmlView](../../mfc/reference/chtmlview-class.md)，从而有效 Web 浏览器视图提供 WebBrowser 控件使应用程序。  
  
### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>创建 Web 浏览器应用程序基于 MFC 文档/视图体系结构  
  
1.  按照中的说明[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)。  
  
2.  在 MFC 应用程序向导[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)页上，确保**文档/视图体系结构**框为选中状态。 (你可以任选一个**单个文档**或**多个文档**，但不是**基于对话框**。)  
  
3.  上[查看生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)页上，使用**基类**下拉列表菜单选择`CHtmlView`。  
  
4.  选择任何其他所需的选项内置于主干应用程序。  
  
5.  单击 **“完成”**。  
  
 WebBrowser 控件支持 Web 浏览的超链接和统一资源定位器 (URL) 导航。 控件维护历史记录列表，用户可以浏览向前和向后通过以前浏览站点、 文件夹和文档。 该控件直接处理导航、 超链接、 历史记录列表、 收藏夹以及安全。 应用程序可以使用 web 浏览器控件作为对主机活动文档的活动文档容器。 因此，将在了格式丰富的文档，如 Microsoft Excel 电子表格或 Word 文档打开和编辑在 WebBrowser 控件中从位置。 WebBrowser 控件也是可以承载任何 ActiveX 控件的 ActiveX 控件容器。  
  
> [!NOTE]
>  WebBrowser ActiveX 控件 (因此`CHtmlView`) 仅供的 Internet Explorer 4.0 版的 Windows 版本下运行的应用程序或更高版本已安装。  
  
 因为`CHtmlView`只需实现 Microsoft Web 浏览器控件，它的支持，用于打印不像其他[CView](../../mfc/reference/cview-class.md)-派生类。 相反，web 浏览器控件实现的打印机用户界面和打印。 因此，`CHtmlView`未不支持打印预览，框架不函数并提供其他打印支持： 例如， [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)， [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)，和[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)，这是其他 MFC 应用程序中可用。  
  
 `CHtmlView` 作为为 Web 浏览器控件，这将使你的应用程序到 Web 或 HTML 页的视图的包装。 该向导创建的重写[OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)在视图类中，提供到 Microsoft Visual c + + Web 站点的导航链接的函数：  
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
    NULL,
    NULL);

} 
```  
  
 您可以使用你自己的替换此站点，或者可以使用[LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource)成员函数以打开位于项目的资源脚本作为视图的默认内容一个 HTML 页。 例如：  
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    LoadFromResource(IDR_HTML1);

} 
```  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MFCIE](http://msdn.microsoft.com/en-us/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)   
 [部署应用程序](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)

