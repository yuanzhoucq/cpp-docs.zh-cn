---
title: "Example: Implementing a Property Page | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "属性页, 实现"
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Example: Implementing a Property Page
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此示例演示如何根据显示的属性页\(允许您更改\) [文档类](../mfc/document-classes.md) 界面的属性。  此接口在visual studio的 [公共环境对象模型示例](../Topic/Common%20Environment%20Object%20Model%20Examples.md) 显示文档\(尽管您将要创建的属性页不关心对象其行为来自何处，只要它们支持正确的接口）。  
  
 此示例基于 [ATLPages示例](../top/visual-cpp-samples.md)。  
  
 若要完成此示例，您需要:  
  
-   使用"添加选件类对话框和ATL属性页向导的[添加ATL属性页选件类](#vcconusing_the_atl_object_wizard)。  
  
-   [编辑对话框资源](#vcconediting_the_dialog_resource) 通过添加 **Document** 接口有趣的属性的新控件。  
  
-   保留属性页网站用户所做的通知[添加消息处理程序](#vcconadding_message_handlers) 更改。  
  
-   添加一些 `#import` 语句和一个typedef在 [管理](#vcconhousekeeping) 部分。  
  
-   验证对象的[重写IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) 传递给属性页。  
  
-   初始化属性页的接口的[重写IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate)。  
  
-   更新使用最新的属性值的对象的[重写IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply)。  
  
-   [显示属性页](#vccontesting_the_property_page) 通过创建一个简单的帮助器对象。  
  
-   将测试属性页的[创建宏](#vcconcreating_a_macro)。  
  
##  <a name="vcconusing_the_atl_object_wizard"></a> 添加ATL属性页选件类  
 首先，创建一个名为 `ATLPages7`的DLL服务器的新ATL项目。  现在使用 [ATL属性页向导](../atl/reference/atl-property-page-wizard.md) 生成属性页。  为属性页 **DocProperties** 然后切换 **短名称Strings** 页设置属性页特定项目。下表所示。  
  
|项|值|  
|-------|-------|  
|标题|TextDocument|  
|文档字符串|VCUE TextDocument属性|  
|Helpfile|*\<blank\>*|  
  
 值在此向导页设置将返回到属性页容器，在调用 **IPropertyPage::GetPageInfo**。  依赖于容器，但是，的内容之后发生在字符串它们通常用于标识您的页给用户。  前缀通常出现在页上的选项，并且文档字符串在状态栏或工具提示会显示\(尽管标准属性框架根本不使用此字符串）。  
  
> [!NOTE]
>  字符串您在此处设置在您的项目中，在字符串资源由向导。  您可以轻松地编辑这些字符串使用资源编辑器，如果需要更改此信息，页面中的代码生成之后。  
  
 单击让 **好** 向导生成的属性页。  
  
##  <a name="vcconediting_the_dialog_resource"></a> 编辑对话框资源  
 既然的属性页中生成的，则需要添加几个控件来表示该页的对话框资源。  添加一个编辑框、静态文本控件和一个复选框并将其ID如下所示:  
  
 ![编辑对话框资源](../atl/media/ppgresourcelabeled.png "PPGResourceLabeled")  
  
 这些控件将用于显示文档及其只读状态的文件名。  
  
> [!NOTE]
>  对话框资源不包括一个帧或命令按钮，也不会有可能需要的选项卡式外观。  这些函数按一个属性页提供例如调用创建该 [OleCreatePropertyFrame](http://msdn.microsoft.com/library/windows/desktop/ms678437)。  
  
##  <a name="vcconadding_message_handlers"></a> 添加消息处理程序  
 在控件中，可以添加消息处理程序更新页面的已更新状态，在控件更改之一的值:  
  
 [!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/CPP/example-implementing-a-property-page_1.h)]  
  
 此代码响应调用到编辑控件或复选框更改 [IPropertyPageImpl::SetDirty](../Topic/IPropertyPageImpl::SetDirty.md)，通知页网站页面已更改。  通常页网站将通过启用或禁用了属性页的一个 **Apply** 按钮响应。  
  
> [!NOTE]
>  在属性页，特性由用户修改的可能需要准确记录，以便可以避免更新未更改的属性。  通过跟踪原始属性值及其代码与用户界面的当前值进行比较的本示例实现，当为时应用更改。  
  
##  <a name="vcconhousekeeping"></a> 管理  
 现在添加有两个 `#import` 语句添加到DocProperties.h，让编译器知道 **Document** 接口:  
  
 [!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/CPP/example-implementing-a-property-page_2.h)]  
  
 您还需要引用 `IPropertyPageImpl` 基类;添加以下 `typedef` 到 **CDocProperties** 选件类:  
  
 [!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/CPP/example-implementing-a-property-page_3.h)]  
  
##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> 重写的IPropertyPageImpl::SetObjects  
 您需要重写的第一个 `IPropertyPageImpl` 方法是 [SetObjects](../Topic/IPropertyPageImpl::SetObjects.md)。  您将添加代码只检查单个对象已通过，它支持您所期望的 **Document** 接口:  
  
 [!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/CPP/example-implementing-a-property-page_4.h)]  
  
> [!NOTE]
>  很有意义支持此页的一个对象，因为您将允许用户设置对象的文件名—只有一个文件可在任何一位置。  
  
##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> 重写的IPropertyPageImpl::Activate  
 当页首次创建后，下一步是初始化与基础对象的属性值的属性页。  
  
 在这种情况下应添加以下成员添加到选件类，因为您用于比较也使用初始属性值，当页面的用户应用这些更改时:  
  
 [!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/CPP/example-implementing-a-property-page_5.h)]  
  
 [激活](../Topic/IPropertyPageImpl::Activate.md) 方法的基类来实现用于创建对话框及其控件负责，因此，您可以重写方法并在调用基类之后添加您的初始化:  
  
 [!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/CPP/example-implementing-a-property-page_6.h)]  
  
 此代码使用 **Document** 接口访问的COM方法属性感兴趣。  然后使用 [CDialogImpl](../atl/reference/cdialogimpl-class.md) 及其基类提供的Win32 API包装显示属性值给用户。  
  
##  <a name="vcconoverride_ipropertypageimpl_apply"></a> 重写的IPropertyPageImpl::Apply  
 当用户要将它们应用于对象的更改，属性页网站将调用 [适用](../Topic/IPropertyPageImpl::Apply.md) 方法。  这是若要执行代码的取消的位置在 **Activate** 的\)，而 **Activate** 采取了从对象的值并使它们在属性页，**Apply** 将控件的值在属性页并推送到对象。  
  
 [!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/CPP/example-implementing-a-property-page_7.h)]  
  
> [!NOTE]
>  [m\_bDirty](../Topic/IPropertyPageImpl::m_bDirty.md) 的检查此实现中开始时避免对象的不必要的更新的初始检查是否 **Apply** 多次调用。  还需要检查确保每个的属性值只会更改导致方法调用 **Document**。  
  
> [!NOTE]
>  **Document** 公开 **FullName** 作为只读属性。  若要更新基于更改文档的文件名对属性页，必须使用 **保存** 方法保存具有不同名称的文件。  因此，在属性页中的代码不必限制自己到获取或设置属性。  
  
##  <a name="vccontesting_the_property_page"></a> 显示属性页  
 若要显示此页，您需要创建一个简单的帮助器对象。  帮助器对象将提供简化显示的单页 **OleCreatePropertyFrame** API连接到一个对象的方法。  此帮助器将模型，以便可以从Visual Basic使用。  
  
 使用 [添加选件类对话框](../ide/add-class-dialog-box.md) 和 [ATL简单对象向导](../atl/reference/atl-simple-object-wizard.md) 生成新选件类和使用 `Helper` 作为其短名称。  一旦创建，添加一个方法根据下表所示。  
  
|项|值|  
|-------|-------|  
|方法名|`ShowPage`|  
|参数|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|  
  
 `bstrCaption` 参数是作为对话框的标题中显示的声明中。  `bstrID` 参数是表示CLSID或属性页的ProgID的字符串显示在中。  `pUnk` 参数是属性。属性页配置对象的 `IUnknown` 指针。  
  
 实现方法如下所示:  
  
 [!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/CPP/example-implementing-a-property-page_8.cpp)]  
  
##  <a name="vcconcreating_a_macro"></a> 创建宏  
 一旦生成项目，可以测试属性页和帮助器对象使用一个简单的宏您在Visual Studio开发环境中创建和运行。  此宏将创建一个帮助器对象，然后调用其 **ShowPage** 方法使用 **DocProperties** 属性页和文档的 **IUnknown** 指针的ProgID当前活动在Visual Studio编辑器。  用于此宏需要的代码如下所示:  
  
```  
Imports EnvDTE  
Imports System.Diagnostics  
  
Public Module AtlPages  
  
    Public Sub Test()  
        Dim Helper  
        Helper = CreateObject("ATLPages7.Helper.1")  
  
        On Error Resume Next  
        Helper.ShowPage( _  
            ActiveDocument.Name, _  
            "ATLPages7Lib.DocumentProperties.1", _  
            DTE.ActiveDocument _  
            )  
    End Sub  
  
End Module  
```  
  
 当您运行此宏，将显示显示文件名的属性页，并且当前活动的只读状态文本文档。  文档的只读状态在开发环境中仅反映能够写入文档;它不影响磁盘上该文件的只读特性的。  
  
## 请参阅  
 [属性页](../atl/atl-com-property-pages.md)   
 [ATLPages示例](../top/visual-cpp-samples.md)