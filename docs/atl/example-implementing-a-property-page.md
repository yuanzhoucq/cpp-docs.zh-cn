---
title: 实现属性页 (ATL) |Microsoft Docs
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
ms.openlocfilehash: 36d3289767d8c8e2eaa2f25889aaff073cf73fce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046246"
---
# <a name="example-implementing-a-property-page"></a>示例： 实现属性页

此示例演示如何生成属性页的显示 （并允许您更改） 的属性[文档类](../mfc/document-classes.md)接口。

示例基于[ATLPages 示例](../visual-cpp-samples.md)。

若要完成此示例中，你将：

- [添加 ATL 属性页类](#vcconusing_the_atl_object_wizard)使用添加类对话框中和 ATL 属性页向导。

- [编辑对话框资源](#vcconediting_the_dialog_resource)通过添加新的有趣属性的控件`Document`接口。

- [添加消息处理程序](#vcconadding_message_handlers)保留属性页网站了解用户所做的更改。

- 添加一些`#import`语句和中的 typedef[内务处理](#vcconhousekeeping)部分。

- [重写 IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects)验证传递到属性页的对象。

- [重写 IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate)初始化属性页的接口。

- [重写 IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply)若要使用的最新的属性值更新对象。

- [显示属性页](#vccontesting_the_property_page)通过创建简单的帮助程序对象。

- [创建一个宏](#vcconcreating_a_macro)，将测试的属性页。

##  <a name="vcconusing_the_atl_object_wizard"></a> 添加 ATL 属性页类

首先，创建新的 ATL 项目调用 DLL 服务器`ATLPages7`。 现在，使用[ATL 属性页向导](../atl/reference/atl-property-page-wizard.md)生成属性页。 为提供的属性页**短名称**的**DocProperties**然后切换到**字符串**页后，可以设置特定于页面属性的项下, 表中所示。

|项|“值”|
|----------|-----------|
|标题|TextDocument|
|文档字符串|VCUE TextDocument 属性|
|帮助文件|*\<保留为空 >*|

在向导的此页上设置的值将在调用时返回到属性页容器`IPropertyPage::GetPageInfo`。 此后对字符串依赖于该容器，但通常它们将用于识别您对用户的页。 标题将通常显示在页面顶部的选项卡中，并可能在状态栏或工具提示中显示文档字符串，（尽管标准属性框架根本不使用此字符串）。

> [!NOTE]
>  此处设置的字符串存储向导为你的项目中的字符串资源。 您可以轻松编辑这些字符串使用资源编辑器，如果您需要为您的页面的代码生成后更改此信息。

单击**确定**让向导生成属性页。

##  <a name="vcconediting_the_dialog_resource"></a> 编辑对话框资源

现在，已生成属性页，您需要将几个控件添加到对话框资源表示您的页面。 添加一个编辑框、 静态文本控件和一个复选框并设置它们的 Id，如下所示：

![编辑对话框资源](../atl/media/ppgresourcelabeled.gif "ppgresourcelabeled")

这些控件将用于显示文档和其只读状态的文件名称。

> [!NOTE]
>  对话框资源不包括框架或命令按钮，也不具有您可能希望的选项卡式的外观。 例如通过调用创建一个属性页框架通过提供这些功能[OleCreatePropertyFrame](/windows/desktop/api/olectl/nf-olectl-olecreatepropertyframe)。

##  <a name="vcconadding_message_handlers"></a> 添加消息处理程序

控制，则你可以添加消息处理程序的任何一个控件的值发生更改时更新脏页的状态：

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

此代码通过调用到编辑控件或复选框所做的更改做出响应[IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)，它通知页已更改的页站点。 页站点将通过启用或禁用的响应通常**应用**属性页帧上的按钮。

> [!NOTE]
>  在您自己属性页中，可能需要跟踪的精确哪些属性已更改的用户，这样可以避免更新未进行过更改的属性。 此示例通过跟踪的原始属性值并将其进行比较 UI 中的当前值时要应用所做的更改来实现该代码。

##  <a name="vcconhousekeeping"></a> 内部管理

现在，添加几个`#import`DocProperties.h 的语句，以便让编译器知道有关`Document`接口：

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

您还需要引用`IPropertyPageImpl`基类; 添加以下**typedef**到`CDocProperties`类：

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> 重写 IPropertyPageImpl::SetObjects

第一个`IPropertyPageImpl`需要重写的方法是[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)。 你将在此处添加代码以检查已传递一个对象，它支持`Document`需要的接口：

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
>  最好支持单个对象的此页上，因为将允许用户设置对象的文件名称，只有一个文件可以位于任何一个位置。

##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> 重写 IPropertyPageImpl::Activate

下一步是首次创建页面时初始化基础对象的属性值的属性页。

在这种情况下应将以下成员添加到类，因为您还将使用的初始属性值进行比较的页的用户应用其更改时：

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

基类实现[激活](../atl/reference/ipropertypageimpl-class.md#activate)方法负责创建对话框中和其控件，因此可以重写此方法，添加你自己的初始化之后调用的基类：

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

此代码使用的 COM 方法`Document`接口，用于获取您感兴趣的属性。 然后，它使用提供的 Win32 API 包装[CDialogImpl](../atl/reference/cdialogimpl-class.md)及其基类以向用户显示的属性值。

##  <a name="vcconoverride_ipropertypageimpl_apply"></a> 重写 IPropertyPageImpl::Apply

当用户想要将其更改应用到的对象时，将调用的属性页站点[应用](../atl/reference/ipropertypageimpl-class.md#apply)方法。 这就是地点中的代码相反`Activate`，而`Activate`对象中的值并推送到属性页面上的控件`Apply`接受的值从属性页上的控件，并将其推送对象。

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
>  针对复选[m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty)在此实现的开头是初始检查以避免不必要的更新的对象，如果`Apply`不止一次调用。 此外，还有针对每个属性值，以确保仅将更改导致方法调用检查`Document`。

> [!NOTE]
> `Document` 公开`FullName`作为只读属性。 若要更新的基于对属性页所做更改的文档的文件名称，您必须使用`Save`方法以使用不同的名称保存该文件。 因此，属性页中的代码不需要限制自身到获取或设置属性。

##  <a name="vccontesting_the_property_page"></a> 显示属性页

若要显示此页，您需要创建一个简单的帮助程序对象。 帮助程序对象将提供的方法，简化了`OleCreatePropertyFrame`用于显示单个页面的 API 连接到单个对象。 将设计此帮助器，以便在 Visual Basic 中使用它。

使用[添加类对话框](../ide/add-class-dialog-box.md)并[ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)生成一个新类并使用`Helper`作为其短名称。 创建后，添加一个方法下, 表中所示。

|项|“值”|
|----------|-----------|
|方法名|`ShowPage`|
|参数|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

*BstrCaption*参数是要显示为对话框的标题的标题。 *BstrID*参数是一个表示 CLSID 或 ProgID 的属性页以显示的字符串。 *PUnk*参数将为`IUnknown`将通过属性页配置其属性的对象的指针。

实现方法，如下所示：

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

##  <a name="vcconcreating_a_macro"></a> 创建一个宏

一旦在生成项目后，你可以测试属性页，并使用一个简单的宏，你可以创建并运行 Visual Studio 开发环境中的帮助器对象。 此宏将创建一个帮助程序对象，然后调用其`ShowPage`方法使用的 ProgID **DocProperties**属性页和`IUnknown`文档在 Visual Studio 编辑器中当前处于活动状态的指针。 为此宏所需的代码如下所示：

```vb
Imports EnvDTE
Imports System.Diagnostics

Public Module AtlPages

Public Sub Test()
    Dim Helper
    Helper = CreateObject("ATLPages7.Helper.1")

    On Error Resume Next
    Helper.ShowPage( ActiveDocument.Name, "ATLPages7Lib.DocumentProperties.1", DTE.ActiveDocument )
End Sub

End Module
```

当您运行此宏时，则将显示属性页显示的文件的名称和当前处于活动状态的文本文档的只读状态。 文档的只读状态仅反映了要写入到开发环境中; 中的文档的功能它不会影响磁盘上的文件的只读属性。

## <a name="see-also"></a>请参阅

[属性页](../atl/atl-com-property-pages.md)<br/>
[ATLPages 示例](../visual-cpp-samples.md)
