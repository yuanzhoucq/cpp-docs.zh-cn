---
title: MFC ActiveX 控件：许可 ActiveX 控件
ms.date: 11/19/2018
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: aaab4ae3bb13790784a66d53b41dbc3a7cdaec89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364605"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC ActiveX 控件：许可 ActiveX 控件

许可支持是 ActiveX 控件的可选功能，允许您控制谁能够使用或分发控件。 （有关许可问题的其他讨论，请参阅[升级现有 ActiveX 控件时](../mfc/upgrading-an-existing-activex-control.md)的许可问题 。

> [!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

本文讨论以下主题：

- [ActiveX 控制许可概述](#_core_overview_of_activex_control_licensing)

- [创建许可控件](#_core_creating_a_licensed_control)

- [许可支持](#_core_licensing_support)

- [自定义 ActiveX 控件的许可](#_core_customizing_the_licensing_of_an_activex_control)

实现许可的 ActiveX 控件允许您作为控件开发人员确定其他人如何使用 ActiveX 控件。 向控件购买者提供控件和 。LIC 文件，同意购买者可以分发控件，但不能分发 。LIC 文件，具有使用控件的应用程序。 这可以防止该应用程序的用户编写使用该控件的新应用程序，而无需首先从您获得控件的许可。

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a>ActiveX 控制许可概述

为了向 ActiveX 控件提供许可支持[，COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)类为`IClassFactory2`接口中的多个函数提供了实现： `IClassFactory2::RequestLicKey``IClassFactory2::GetLicInfo`和`IClassFactory2::CreateInstanceLic`。 当容器应用程序开发人员请求创建控件的实例时，将调用 以`GetLicInfo`验证控件 是否。LIC 文件存在。 如果控件已获得许可，则可以创建控件的实例并将其放置在容器中。 开发人员完成容器应用程序的构造后，将发出另一个函数调用，此时将`RequestLicKey`调用 。。 此功能向容器应用程序返回许可证密钥（简单字符串）。 然后，返回的密钥嵌入到应用程序中。

下图演示了将在开发容器应用程序期间使用的 ActiveX 控件的许可证验证。 如前所述，容器应用程序开发人员必须具有正确的 。安装在开发计算机上的 LIC 文件以创建控件的实例。

![开发时验证了已获许可的 ActiveX 控件](../mfc/media/vc374d1.gif "开发时验证了已获许可的 ActiveX 控件") <br/>
开发期间授权 ActiveX 控件的验证

下图中显示了下一个过程，当最终用户运行容器应用程序时。"

启动应用程序时，通常需要创建控件的实例。 容器通过调用`CreateInstanceLic`、传递嵌入的许可证密钥作为参数来实现此目的。 然后，在嵌入式许可证密钥和控件自己的许可证密钥副本之间进行字符串比较。 如果匹配成功，将创建控件的实例，并且应用程序继续正常执行。 请注意， .LIC 文件不需要存在于控件用户的计算机上。

![执行时验证了已获许可的 ActiveX 控件](../mfc/media/vc374d2.gif "执行时验证了已获许可的 ActiveX 控件") <br/>
执行期间授权 ActiveX 控件的验证

控制许可由两个基本组件组成：控制实现 DLL 和许可证文件中的特定代码。 该代码由两个（或可能三个）函数调用和一个字符串组成，其后称为"许可证字符串"，其中包含版权通知。 这些调用和许可证字符串位于控件实现 （中。CPP）文件。 由 ActiveX 控制向导生成的许可证文件是带有版权声明的文本文件。 它使用 项目名称与 命名。LIC 扩展，例如 SAMPLE。LIC. 如果需要设计时使用，许可控件必须附带许可证文件。

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a>创建许可控件

当您使用 ActiveX 控制向导创建控制框架时，可以轻松包括许可支持。 当您指定控件应具有运行时许可证时，ActiveX 控制向导会将代码添加到控件类以支持许可。 该代码由使用密钥和许可证文件进行许可证验证的功能组成。 还可以修改这些功能以自定义控件许可。 有关许可证自定义的详细信息，请参阅本文后面的["自定义 ActiveX 控件许可](#_core_customizing_the_licensing_of_an_activex_control)"。

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>在创建控制项目时使用 ActiveX 控制向导添加对许可的支持

1. 在[创建 MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)中使用说明。 ActiveX 控件向导**的应用程序设置**页包含使用运行时许可证创建控件的选项。

ActiveX 控制向导现在生成一个 ActiveX 控制框架，其中包含基本许可支持。 有关许可代码的详细说明，请参阅下一个主题。

## <a name="licensing-support"></a><a name="_core_licensing_support"></a>许可支持

当您使用 ActiveX 控制向导向 ActiveX 控件添加许可支持时，ActiveX 控件向导会添加声明和实现许可功能的代码将添加到控制标头和实现文件中。 此代码由`VerifyUserLicense`成员函数和`GetLicenseKey`成员函数组成，该函数覆盖[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)中的默认实现。 这些功能检索和验证控制许可证。

> [!NOTE]
> 第三个成员函数`VerifyLicenseKey`不是由 ActiveX 控制向导生成的，但可以重写以自定义许可证密钥验证行为。

这些成员函数是：

- [验证用户许可证](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   通过检查系统是否存在控制许可证文件，验证控件是否允许设计时使用。 此函数由框架调用作为处理`IClassFactory2::GetLicInfo`和`IClassFactory::CreateInstanceLic`的一部分。

- [获取许可密钥](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   从控件 DLL 请求唯一的密钥。 此密钥嵌入到容器应用程序中，并在以后与`VerifyLicenseKey`结合使用来创建控件的实例。 此函数由框架调用作为处理`IClassFactory2::RequestLicKey`的一部分。

- [验证许可证密钥](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   验证嵌入密钥和控件的唯一键是否相同。 这允许容器创建控件的实例供其使用。 此函数由框架调用作为处理`IClassFactory2::CreateInstanceLic`的一部分，可以重写以提供许可证密钥的自定义验证。 默认实现执行字符串比较。 有关详细信息，请参阅在本文后面的自定义[ActiveX 控件的许可](#_core_customizing_the_licensing_of_an_activex_control)。

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a>标题文件修改

ActiveX 控制向导将以下代码放在控件头文件中。 在此示例中，`CSampleCtrl``factory`将声明对象的两个成员函数，一个函数验证控件的存在。LIC 文件和其他检索要在包含控件的应用程序中使用的许可证密钥的文件：

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a>实现文件修改

ActiveX 控制向导在控件实现文件中放置以下两个语句，以声明许可证文件名和许可证字符串：

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> 如果以任何方式修改`szLicString`，还必须修改控件 中的第一行。LIC 文件或许可将无法正常运行。

ActiveX 控制向导在控件实现文件中放置以下代码，以定义控件类和`VerifyUserLicense``GetLicenseKey`函数：

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

最后 **，ActiveX 控件向导**修改控件项目。IDL 文件。 **许可**关键字将添加到控件的 coclass 声明中，如以下示例所示：

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a>自定义 ActiveX 控件的许可

由于`VerifyUserLicense` `GetLicenseKey`，`VerifyLicenseKey`和 声明为控件工厂类的虚拟成员函数，因此可以自定义控件的许可行为。

例如，您可以通过重写`VerifyUserLicense`或`VerifyLicenseKey`成员函数为控件提供多个级别的许可。 在此函数中，您可以根据检测到的许可证级别调整向用户公开的属性或方法。

还可以向`VerifyLicenseKey`函数添加代码，该函数提供自定义方法，通知用户控件创建失败。 例如，在`VerifyLicenseKey`成员函数中，可以显示一个消息框，指出控件未能初始化以及原因。

> [!NOTE]
> 自定义 ActiveX 控制许可证验证的另一种方法是检查注册数据库中的特定注册表项，而不是调用`AfxVerifyLicFile`。 有关默认实现的示例，请参阅本文的["实现文件修改"](#_core_implementation_file_modifications)部分。

有关许可问题的其他讨论，请参阅[升级现有 ActiveX 控件时](../mfc/upgrading-an-existing-activex-control.md)的许可问题。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制向导](../mfc/reference/mfc-activex-control-wizard.md)
