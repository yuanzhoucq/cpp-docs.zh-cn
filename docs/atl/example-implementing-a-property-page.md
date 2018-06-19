---
title: 实现属性页 (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 139bdd9076e99139f4da105b4bb2b375689efe15
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363708"
---
# <a name="example-implementing-a-property-page"></a>示例： 实现的属性页
此示例演示如何生成显示 （并允许您更改） 的属性的属性页[文档类](../mfc/document-classes.md)接口。  
  
 示例基于[ATLPages 示例](../visual-cpp-samples.md)。  
  
 若要完成此示例中，你将：  
  
- [添加 ATL 属性页类](#vcconusing_the_atl_object_wizard)使用添加类对话框中和 ATL 属性页向导。  
  
- [编辑对话框资源](#vcconediting_the_dialog_resource)通过添加新控件的有趣属性**文档**接口。  
  
- [添加消息处理程序](#vcconadding_message_handlers)以保持属性页站点的通知用户所做的更改。  
  
-   添加一些`#import`语句和中的 typedef[内务处理](#vcconhousekeeping)部分。  
  
- [重写 IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects)验证传递给属性页的对象。  
  
- [重写 IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate)初始化属性页的接口。  
  
- [重写 IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply)若要使用的最新的属性值更新对象。  
  
- [显示的属性页](#vccontesting_the_property_page)通过创建一个简单的帮助器对象。  
  
- [创建一个宏](#vcconcreating_a_macro)将测试的属性页。  
  
##  <a name="vcconusing_the_atl_object_wizard"></a> 添加 ATL 属性页类  
 首先，创建新的 ATL 项目调用 DLL 服务器`ATLPages7`。 现在使用[ATL 属性页向导](../atl/reference/atl-property-page-wizard.md)生成属性页。 为提供的属性页**短名称**的**DocProperties**然后切换到**字符串**页后，可以设置特定于属性页的项，如下面的表中所示。  
  
|项|值|  
|----------|-----------|  
|标题|TextDocument|  
|文档字符串|VCUE TextDocument 属性|  
|Helpfile|*\<空白 >*|  
  
 在向导的此页设置的值将返回到属性页容器，当它调用**IPropertyPage::GetPageInfo**。 会发生什么情况字符串后，依赖于容器，但通常它们将用于识别您对用户的页。 标题将通常显示在你的页面顶部的选项卡和文档字符串可能会显示在状态栏或工具提示，（尽管标准属性框架根本不使用此字符串）。  
  
> [!NOTE]
>  你在此处设置的字符串存储向导为你的项目中的字符串资源。 你可以方便地编辑这些字符串使用资源编辑器，如果你需要在生成你的页的代码后更改此信息。  
  
 单击**确定**让向导生成属性页。  
  
##  <a name="vcconediting_the_dialog_resource"></a> 编辑对话框资源  
 现在，已生成属性页，你将需要将几个控件添加到对话框资源表示你的页面。 添加编辑框、 静态文本控件和复选框，并设置其 Id，如下所示：  
  
 ![编辑对话框资源](../atl/media/ppgresourcelabeled.gif "ppgresourcelabeled")  
  
 这些控件将用于显示文档和其只读状态的文件名称。  
  
> [!NOTE]
>  对话框资源不包含框架或命令按钮，也不具有您可能希望的选项卡式的外观。 这些功能提供的属性页框架，例如通过调用创建一个[OleCreatePropertyFrame](http://msdn.microsoft.com/library/windows/desktop/ms678437)。  
  
##  <a name="vcconadding_message_handlers"></a> 添加消息处理程序  
 控制，你可以添加消息处理程序来更新脏页的状态，任何一个控件的值更改时：  
  
 [!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]  
  
 此代码响应由调用编辑控件或复选框对所做的更改[IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)，它通知页已更改的页站点。 通常页网站会响应通过启用或禁用**应用**属性页帧上的按钮。  
  
> [!NOTE]
>  在你自己属性页中，你可能需要跟踪的精确哪些属性更改了用户，以便你可以避免更新尚未更改的属性。 本示例实现该代码通过跟踪的原始属性值以及对它们进行比较 UI 中的当前值时要应用所做的更改。  
  
##  <a name="vcconhousekeeping"></a> 管理  
 现在，将添加几个`#import`向 DocProperties.h 语句，以便编译器知道**文档**接口：  
  
 [!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]  
  
 你还需要参阅`IPropertyPageImpl`基类; 将以下代码添加`typedef`到**CDocProperties**类：  
  
 [!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]  
  
##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> 重写 IPropertyPageImpl::SetObjects  
 第一个`IPropertyPageImpl`需要重写的方法是[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)。 此处将添加代码以检查已传递一个对象，并确保它支持**文档**你希望的接口：  
  
 [!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]  
  
> [!NOTE]
>  有必要为此页支持单个对象，因为你将允许用户设置对象的文件名称 — 只有一个文件可以位于任何一个位置。  
  
##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> 重写 IPropertyPageImpl::Activate  
 下一步是首次创建页面时初始化基础对象的属性值的属性页。  
  
 在这种情况下应将以下成员添加到类中，因为你将还使用的初始属性值进行比较时的页面的用户应用其更改：  
  
 [!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]  
  
 基类实现[激活](../atl/reference/ipropertypageimpl-class.md#activate)方法负责创建对话框中和其控件，以便你可以重写此方法并添加你自己的初始化后调用的基类：  
  
 [!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]  
  
 此代码使用的 COM 方法**文档**接口以获取你感兴趣的属性。 然后，它使用提供的 Win32 API 包装[CDialogImpl](../atl/reference/cdialogimpl-class.md)和其基的类，以向用户显示的属性值。  
  
##  <a name="vcconoverride_ipropertypageimpl_apply"></a> 重写 IPropertyPageImpl::Apply  
 当用户想要将其更改应用于对象时，将调用属性页站点[应用](../atl/reference/ipropertypageimpl-class.md#apply)方法。 这是进行中的代码的反向操作的位置**激活**— 而**激活**所用时间从对象的值，它们推送到属性页上，控件**应用**采用属性页上的控件中的值并将它们推送到对象。  
  
 [!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]  
  
> [!NOTE]
>  针对检查[m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty)在开始时此实现的是初始检查，以避免不必要的更新的对象，如果**应用**调用一次以上。 还有针对每个属性值，以确保仅更改导致对的方法调用的检查**文档**。  
  
> [!NOTE]
> **文档**公开**FullName**作为只读属性。 若要更新的基于对属性页所做更改文档的文件名称，你必须使用**保存**方法使用不同的名称保存文件。 因此，属性页中的代码不需要限制本身为获取或设置属性。  
  
##  <a name="vccontesting_the_property_page"></a> 显示的属性页  
 若要显示此页，你需要创建一个简单的帮助器对象。 帮助程序对象将提供的方法，它简化了**OleCreatePropertyFrame**用于显示一页的 API 连接到单个对象。 将设计此帮助器，以便可以从 Visual Basic 使用它。  
  
 使用[添加类对话框](../ide/add-class-dialog-box.md)和[ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)生成一个新类并使用`Helper`作为其短名称。 创建后，添加一个方法下, 表中所示。  
  
|项|值|  
|----------|-----------|  
|方法名|`ShowPage`|  
|参数|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|  
  
 `bstrCaption`参数是要为对话框中的标题显示的标题。 `bstrID`参数是表示 CLSID 或 ProgID 的属性页以显示一个字符串。 `pUnk`参数将为`IUnknown`将通过属性页配置其属性的对象的指针。  
  
 实现该方法，如下所示：  
  
 [!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]  
  
##  <a name="vcconcreating_a_macro"></a> 创建一个宏  
 后生成项目后，你可以测试的属性页和使用一个简单的宏，你可以创建和运行在 Visual Studio 开发环境中的帮助程序对象。 此宏将创建一个帮助程序对象，然后调用其**显示页面**方法使用的 ProgID **DocProperties**属性页和**IUnknown**文档的指针在 Visual Studio 编辑器中当前处于活动状态。 为此宏所需的代码所示：  
  
```  
Imports EnvDTE  
Imports System.Diagnostics  
 
Public Module AtlPages  
 
    Public Sub Test()  
    Dim Helper  
    Helper = CreateObject("ATLPages7.Helper.1")  
 
    On Error Resume Next  
    Helper.ShowPage(_ 
    ActiveDocument.Name,
    _ 
 "ATLPages7Lib.DocumentProperties.1",
    _ 
    DTE.ActiveDocument _)  
    End Sub  
 
End Module  
```  
  
 当你运行此宏时，则将显示属性页上显示的文件名称和当前处于活动状态的文本文档的只读状态。 文档的只读状态仅反映用于编写到开发环境中; 中的文档的功能它不会影响磁盘上的文件的只读属性。  
  
## <a name="see-also"></a>请参阅  
 [属性页](../atl/atl-com-property-pages.md)   
 [ATLPages 示例](../visual-cpp-samples.md)

