---
title: 创建一个 Web 浏览器样式的 MFC 应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
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
ms.openlocfilehash: 71312a1dfa70ca3fd83242f6f706654c08a4973c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217662"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>创建 Web 浏览器样式的 MFC 应用程序
本地文件系统中和在网络上，Web 浏览器样式的应用程序可以从 （如 HTML 或活动文档） Internet 或 intranet，以及文件夹访问信息。 通过派生应用程序的视图类从[CHtmlView](../../mfc/reference/chtmlview-class.md)，从而有效地通过为视图提供 WebBrowser 控件使应用程序的 Web 浏览器。  
  
### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>若要创建基于 MFC 文档/视图体系结构上的 Web 浏览器应用程序  
  
1.  按照中的说明[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)。  
  
2.  在 MFC 应用程序向导[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)页上，请确保**文档/视图体系结构**框处于选中状态。 (你可以任选**单个文档**或**多个文档**，但不是**基于对话框**。)  
  
3.  上[查看生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)页上，使用**基类**下拉列表菜单选择`CHtmlView`。  
  
4.  选择任何其他所需的选项内置主干应用程序。  
  
5.  单击 **“完成”**。  
  
 WebBrowser 控件支持的 Web 浏览通过超链接和统一资源定位器 (URL) 导航。 控件维护历史记录列表，从而允许用户浏览向前和向后移动之前浏览站点、 文件夹和文档。 该控件直接处理导航、 超链接、 历史记录列表、 收藏夹以及安全性。 应用程序可以使用 web 浏览器控件作为活动文档容器到主机活动文档。 因此，具有丰富格式的文档，例如 Microsoft Excel 电子表格或 Word 文档可以打开和就地编辑从 web 浏览器控件中。 WebBrowser 控件也是可以托管任何 ActiveX 控件的 ActiveX 控件容器。  
  
> [!NOTE]
>  WebBrowser ActiveX 控件 (并因此`CHtmlView`) 仅适用于 Windows 版本的 Internet Explorer 4.0 下运行的应用程序或更高版本已安装。  
  
 因为`CHtmlView`只需实现 Microsoft Web 浏览器控件，它的支持，用于打印不与其他值一样[CView](../../mfc/reference/cview-class.md)-派生的类。 相反，web 浏览器控件实现打印机用户界面和打印。 因此， `CHtmlView` does 不支持打印预览，并在 framework 不提供其他打印支持功能： 例如， [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)， [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)，并[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)，这是其他 MFC 应用程序中可用。  
  
 `CHtmlView` 充当 Web 浏览器控件，这将使你的应用程序到 Web 或 HTML 页的视图的包装器。 该向导创建的重写[OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)在视图类中，提供 Microsoft Visual c + + 网站上的导航链接的函数：  
  
```cpp
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.  
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
        NULL,
        NULL);
}
```

可以使用您自己，替换此站点也可以使用[LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource)成员函数，以打开位于项目的资源脚本作为默认内容视图的 HTML 页。 例如：  
  
```cpp
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.  
    LoadFromResource(IDR_HTML1);
}
```  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MFCIE](https://msdn.microsoft.com/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)   
 [部署应用程序](https://msdn.microsoft.com/4ff8881d-0daf-47e7-bfe7-774c625031b4)

