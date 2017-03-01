---
title: "创建一个 Web 浏览器样式的 MFC 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfcweb.project
dev_langs:
- C++
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications, creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ccfb093a65c3f9a72b6180c4f415a92ebaf18684
ms.lasthandoff: 02/24/2017

---
# <a name="creating-a-web-browser-style-mfc-application"></a>创建 Web 浏览器样式的 MFC 应用程序
本地文件系统中和在网络上，Web 浏览器样式的应用程序可以从 （如 HTML 或活动文档） Internet 或 intranet，以及文件夹访问信息。 通过派生应用程序的视图类从[CHtmlView](../../mfc/reference/chtmlview-class.md)，从而有效地通过提供使用 WebBrowser 控件的视图使应用程序的 Web 浏览器。  
  
### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>若要创建基于 MFC 文档/视图体系结构的 Web 浏览器应用程序  
  
1.  按照提示进行操作[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)。  
  
2.  在 MFC 应用程序向导[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)页上，请确保**文档/视图体系结构**框处于选中状态。 (您可以选择**单个文档**或**多个文档**，但不是**基于对话框**。)  
  
3.  在[查看生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)页上，使用**基类**下拉菜单中选择`CHtmlView`。  
  
4.  选择任何其他所需的选项内置于主干应用程序。  
  
5.  单击 **“完成”**。  
  
 WebBrowser 控件支持通过超链接和统一资源定位器 (URL) 导航的 Web 浏览。 该控件维护历史记录列表，用户可以浏览向前和顺序进行逆向分析以前浏览过的站点、 文件夹和文档。 该控件直接处理导航、 超链接、 历史记录列表、 收藏夹和安全。 应用程序可以使用 web 浏览器控件作为活动文档容器对主机活动文档。 因此，具有丰富格式的文档，如 Microsoft Excel 电子表格或 Word 文档可以打开和就地编辑从 web 浏览器控件中。 Web 浏览器控件也是可以承载任何 ActiveX 控件的 ActiveX 控件容器。  
  
> [!NOTE]
>  WebBrowser ActiveX 控件 (并因此`CHtmlView`) 仅适用于运行的 Internet Explorer 4.0 中的 Windows 版本的应用程序或更高版本已安装。  
  
 因为`CHtmlView`只打印并不像其他实现 Microsoft Web 浏览器控件，它支持[CView](../../mfc/reference/cview-class.md)的派生类。 相反，web 浏览器控件实现打印机用户界面和打印。 因此，`CHtmlView`未不支持打印预览、 和框架不提供对其他打印的支持功能︰ 例如， [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)， [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)，和[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)，其他 MFC 应用程序中提供了这些。  
  
 `CHtmlView`充当 Web 浏览器控件，这将使您的应用程序视图中的拖到某一 Web 或 HTML 页的包装器。 该向导创建的重写[OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)函数在视图类中，并提供指向 Microsoft Visual c + + 网站上的导航链接︰  
  
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
  
 您可以使用自己，替换此站点也可以使用[LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource)成员函数，以打开该视图的默认内容作为驻留在项目的资源脚本中的 HTML 页。 例如:   
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    LoadFromResource(IDR_HTML1);

} 
```  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 MFCIE](http://msdn.microsoft.com/en-us/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)   
 [部署应用程序](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)


