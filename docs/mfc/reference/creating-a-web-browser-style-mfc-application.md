---
title: "创建 Web 浏览器样式的 MFC 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcweb.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC, Web 应用程序"
  - "Web 应用程序, 创建"
  - "Web 浏览器"
  - "Web 浏览器, 从 MFC 体系结构创建"
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 创建 Web 浏览器样式的 MFC 应用程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Web 浏览器样式的应用程序除了可以访问本地文件系统和网络上的文件夹外，还可以访问 Internet（如 HTML 或活动文档）或者 Intranet 上的信息。  通过从 [CHtmlView](../../mfc/reference/chtmlview-class.md) 导出应用程序的视图类，并利用 WebBrowser 控件提供视图，有效地使应用程序成为 Web 浏览器。  
  
### 创建基于 MFC 文档\/视图结构的 Web 浏览器应用程序  
  
1.  按照[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)中的指导操作。  
  
2.  在 MFC 应用程序向导的[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)页中，确保选定“文档\/视图结构支持”框。（可以选择“单文档”或者“多文档”，但不能选择“基于对话框”。）  
  
3.  在[查看生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)页中，使用“基类”下拉菜单选择 `CHtmlView`。  
  
4.  选择任何其他要内置到主干应用程序中的选项。  
  
5.  单击**“完成”**。  
  
 WebBrowser 控件通过超链接和统一资源定位器 \(URL\) 导航支持 Web 浏览。  该控件维护历史记录列表，允许用户在以前浏览过的站点、文件夹和文档中向前和向后浏览。  该控件直接处理导航、超链接、历史记录列表、收藏夹和安全性。  应用程序可以将 WebBrowser 控件用作同样承载活动文档的活动文档容器。  因此，具有丰富格式的文档（如 Microsoft Excel 电子表格或 Word 文档）能从 WebBrowser 控件中就地打开和编辑。  WebBrowser 控件也是可承载任何 ActiveX 控件的 ActiveX 控件容器。  
  
> [!NOTE]
>  WebBrowser ActiveX 控件（因此是 `CHtmlView`）仅适用于在安装有 Internet Explorer 4.0 或更高版本的 Windows 版本下运行的应用程序。  
  
 因为 `CHtmlView` 仅实现 Microsoft Web 浏览器控件，它对打印的支持不像其他 [CView](../../mfc/reference/cview-class.md) 导出的类。  相反，WebBrowser 控件实现打印机用户界面和打印。  因此，`CHtmlView` 不支持打印预览，并且框架不提供其他打印支持函数：例如，[CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)、[CView::OnBeginPrinting](../Topic/CView::OnBeginPrinting.md) 和 [CView::OnEndPrinting](../Topic/CView::OnEndPrinting.md)，而它们在其他 MFC 应用程序中是可用的。  
  
 用作 `CHtmlView` Web 浏览器控件的包装，为应用程序提供在 Web 或 HTML 页上的视图。  向导在视图类中创建 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 函数的一个重写，以提供到 Microsoft Visual C\+\+ 网站的导航链接：  
  
```  
void CWebView::OnInitialUpdate()  
{  
   CHtmlView::OnInitialUpdate();  
  
   // TODO: This code navigates to a popular spot on the web.  
   //  change the code to go where you'd like.  
   Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),NULL,NULL);  
}  
```  
  
 可以用自己的站点替换该站点，也可以使用 [LoadFromResource](../Topic/CHtmlView::LoadFromResource.md) 成员函数打开驻留在项目资源脚本中的一个 HTML 页作为视图的默认内容。  例如：  
  
```  
void CWebView::OnInitialUpdate()  
{  
   CHtmlView::OnInitialUpdate();  
  
   // TODO: This code navigates to a popular spot on the web.  
   //  change the code to go where you'd like.  
   LoadFromResource(IDR_HTML1);  
}  
```  
  
## 请参阅  
 [MFC Sample MFCIE](http://msdn.microsoft.com/zh-cn/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-cn/4ff8881d-0daf-47e7-bfe7-774c625031b4)