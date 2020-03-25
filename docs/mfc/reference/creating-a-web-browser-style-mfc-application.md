---
title: 创建 Web 浏览器样式的 MFC 应用程序
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: e02e928f65ab4cd918e730135abc62ed3237decf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215119"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>创建 Web 浏览器样式的 MFC 应用程序

Web 浏览器样式的应用程序可以从 Internet 访问信息（如 HTML 或活动文档）或 intranet，以及本地文件系统中和网络上的文件夹。 通过从[CHtmlView](../../mfc/reference/chtmlview-class.md)派生应用程序的视图类，可以通过使用 WebBrowser 控件提供视图，有效地将应用程序设置为 Web 浏览器。

## <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>创建基于 MFC 文档/视图体系结构的 Web 浏览器应用程序

1. 按照[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)中的说明进行操作。

1. 在 "MFC 应用程序向导" 的 "[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)" 页上，确保选中 "**文档/视图体系结构**" 框。 （您可以选择**单个文档**或**多个文档**，但不能选择**基于对话框**。）

1. 在 "[查看生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)" 页上，使用 "**基类**" 下拉菜单选择 `CHtmlView`。

1. 选择要内置到主干应用程序的任何其他选项。

1. 单击“完成”。

WebBrowser 控件支持通过超链接和统一资源定位符（URL）导航进行 Web 浏览。 控件维护历史记录列表，使用户能够在以前浏览过的网站、文件夹和文档中向前和向后浏览。 控件直接处理导航、超链接、历史记录列表、收藏夹和安全性。 应用程序还可以使用 WebBrowser 控件作为活动文档容器来承载活动文档。 因此，可以从 WebBrowser 控件内就地打开和编辑格式丰富的文档（如 Microsoft Excel 电子表格或 Word 文档）。 WebBrowser 控件也是可承载任何 ActiveX 控件的 ActiveX 控件容器。

> [!NOTE]
> WebBrowser ActiveX 控件（因此 `CHtmlView`）仅适用于在安装了 Internet Explorer 4.0 或更高版本的 Windows 版本下运行的应用程序。

由于 `CHtmlView` 仅实现了 Microsoft Web 浏览器控件，因此它对打印的支持与其他[CView](../../mfc/reference/cview-class.md)派生类不同。 而是通过 WebBrowser 控件实现打印机用户界面和打印。 因此，`CHtmlView` 不支持打印预览，并且该框架不提供其他打印支持函数：例如， [cview：： OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)、 [Cview：： OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)和[CView：： OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)，这些函数在其他 MFC 应用程序中可用。

`CHtmlView` 充当 Web 浏览器控件的包装器，这为应用程序提供了一个视图到 Web 或 HTML 页面的视图。 向导将在视图类中创建对[OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)函数的重写，并提供指向 Microsoft Visual C++网站的导航链接：

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.docs.microsoft.com/"),
        NULL,
        NULL);
}
```

您可以将此站点替换为您自己的网站，也可以使用[LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource)成员函数打开作为视图的默认内容驻留在项目的资源脚本中的 HTML 页面。 例如：

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>另请参阅

[MFC 示例 MFCIE](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet)<br/>
[MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)<br/>
[设置编译器和生成属性](../../build/working-with-project-properties.md)<br/>
[属性页](../../build/reference/property-pages-visual-cpp.md)<br/>
[设置编译器和生成属性](../../build/working-with-project-properties.md)
