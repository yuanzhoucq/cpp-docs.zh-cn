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
ms.openlocfilehash: 4fe2fcf63cce02ed6c1c9943e6d0fe6ffab00a92
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622372"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC ActiveX 控件：许可 ActiveX 控件

许可支持是 ActiveX 控件的一项可选功能，可用于控制谁可以使用或分发控件。 （有关许可问题的其他讨论，请参阅[升级现有 ActiveX 控件](upgrading-an-existing-activex-control.md)中的许可问题。）

> [!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

本文讨论以下主题：

- [ActiveX 控件授权概述](#_core_overview_of_activex_control_licensing)

- [创建授权控件](#_core_creating_a_licensed_control)

- [许可支持](#_core_licensing_support)

- [自定义 ActiveX 控件的许可](#_core_customizing_the_licensing_of_an_activex_control)

实现许可的 ActiveX 控件允许你作为控制开发人员来确定其他人如何使用 ActiveX 控件。 向控件购买者提供控制和。许可证文件，并同意买方可能会分发控件，而不是。许可证文件，其中包含使用控件的应用程序。 这会阻止该应用程序的用户编写使用该控件的新应用程序，而无需先向用户授予控件授权。

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a>ActiveX 控件授权概述

为提供对 ActiveX 控件的许可支持， [COleObjectFactory](reference/coleobjectfactory-class.md)类为接口中的几个函数提供实现 `IClassFactory2` ： `IClassFactory2::RequestLicKey` 、 `IClassFactory2::GetLicInfo` 和 `IClassFactory2::CreateInstanceLic` 。 当容器应用程序开发人员发出创建控件实例的请求时，将调用以 `GetLicInfo` 验证控件。许可证文件存在。 如果控件已获得许可，则可以创建控件的一个实例并将其放置在容器中。 开发人员构建完容器应用程序后，将进行另一个函数调用 `RequestLicKey` 。 此函数为容器应用程序返回许可证密钥（一个简单的字符串）。 然后，将在应用程序中嵌入返回的键。

下图演示了在开发容器应用程序的过程中将使用的 ActiveX 控件的许可证验证。 如前文所述，容器应用程序开发人员必须具有相应的。开发计算机上安装的许可证文件，用于创建控件的实例。

![开发时验证了已获许可的 ActiveX 控件](../mfc/media/vc374d1.gif "开发时验证了已获许可的 ActiveX 控件") <br/>
开发期间授权 ActiveX 控件的验证

下图中显示的下一个过程在最终用户运行容器应用程序时发生。

启动应用程序时，通常需要创建控件的实例。 容器通过调用来实现此过程 `CreateInstanceLic` ，并将嵌入式许可证密钥作为参数传递。 然后，在嵌入的许可证密钥与该控件自己的许可证密钥副本之间进行字符串比较。 如果匹配成功，则会创建控件的实例，并且应用程序将继续正常执行。 请注意，。许可证文件不需要存在于控件用户的计算机上。

![执行时验证了已获许可的 ActiveX 控件](../mfc/media/vc374d2.gif "执行时验证了已获许可的 ActiveX 控件") <br/>
执行期间授权 ActiveX 控件的验证

控制授权包括两个基本组件：控件实现 DLL 中的特定代码和许可证文件。 此代码由两个（或可能为三个）函数调用和一个字符串（以后称为 "许可证字符串"）组成，其中包含版权声明。 这些调用和许可证字符串在控件实现（。CPP）文件。 由 ActiveX 控件向导生成的许可证文件是带有版权声明的文本文件。 它使用项目名称和来命名。许可证扩展，例如示例。许可证. 如果需要设计时使用，则许可的控件必须附带许可证文件。

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a>创建授权控件

使用 ActiveX 控件向导创建控件框架时，可以轻松地包含许可支持。 指定控件应具有运行时许可证时，ActiveX 控件向导会将代码添加到控件类以支持授权。 该代码包含使用密钥和许可证文件进行许可证验证的函数。 还可以修改这些函数以自定义控件授权。 有关许可证自定义的详细信息，请参阅本文后面的[自定义 ActiveX 控件的许可](#_core_customizing_the_licensing_of_an_activex_control)。

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>在创建控件项目时添加 ActiveX 控件向导对授权的支持

1. 使用[创建 MFC ActiveX 控件](reference/creating-an-mfc-activex-control.md)中的说明。 ActiveX 控件向导的 "**应用程序设置**" 页包含用运行时许可证创建控件的选项。

ActiveX 控件向导现在将生成一个包含基本许可支持的 ActiveX 控件框架。 有关许可代码的详细说明，请参阅下一主题。

## <a name="licensing-support"></a><a name="_core_licensing_support"></a>许可支持

使用 ActiveX 控件向导将许可支持添加到 ActiveX 控件时，ActiveX 控件向导会添加声明并实现授权功能的代码，并将其添加到控件头和实现文件中。 此代码由 `VerifyUserLicense` 成员函数和 `GetLicenseKey` 成员函数组成，后者重写[COleObjectFactory](reference/coleobjectfactory-class.md)中找到的默认实现。 这些函数检索并验证控制许可证。

> [!NOTE]
> 第三个成员函数 `VerifyLicenseKey` 不是由 ActiveX 控件向导生成，但可以重写以自定义许可证密钥验证行为。

这些成员函数包括：

- [VerifyUserLicense](reference/coleobjectfactory-class.md#verifyuserlicense)

   通过检查系统中是否存在控制许可证文件来验证控件是否允许设计时使用。 此函数在处理和时由框架调用 `IClassFactory2::GetLicInfo` `IClassFactory::CreateInstanceLic` 。

- [GetLicenseKey](reference/coleobjectfactory-class.md#getlicensekey)

   从控件 DLL 请求一个唯一键。 此键嵌入在容器应用程序中，稍后将与一起使用， `VerifyLicenseKey` 以创建控件的实例。 在处理过程中，框架将调用此函数 `IClassFactory2::RequestLicKey` 。

- [VerifyLicenseKey](reference/coleobjectfactory-class.md#verifylicensekey)

   验证嵌入密钥和控件的唯一键是否相同。 这允许容器为其使用创建控件的实例。 此函数由框架在处理过程中调用 `IClassFactory2::CreateInstanceLic` ，可以重写以提供对许可证密钥的自定义验证。 默认实现执行字符串比较。 有关详细信息，请参阅本文后面的[自定义 ActiveX 控件的许可](#_core_customizing_the_licensing_of_an_activex_control)。

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a>标头文件修改

ActiveX 控件向导将以下代码放在控件头文件中。 在此示例中，声明了的对象的两个成员函数 `CSampleCtrl` `factory` ，一个用于验证控件是否存在。许可证文件，另一个检索要在包含控件的应用程序中使用的许可证密钥：

[!code-cpp[NVC_MFC_AxUI#39](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a>实现文件修改

ActiveX 控件向导在控件实现文件中放置以下两个语句，以声明许可证文件名和许可证字符串：

[!code-cpp[NVC_MFC_AxUI#40](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> 如果 `szLicString` 以任何方式进行修改，则还必须修改控件中的第一行。许可证文件或授权将无法正常运行。

ActiveX 控件向导将以下代码放置在控件实现文件中，以定义控件类 `VerifyUserLicense` 和 `GetLicenseKey` 函数：

[!code-cpp[NVC_MFC_AxUI#41](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

最后， **ActiveX 控件向导**会修改控件项目。IDL 文件。 **授权**的关键字将添加到控件的 coclass 声明中，如下面的示例中所示：

[!code-cpp[NVC_MFC_AxUI#42](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a>自定义 ActiveX 控件的许可

由于 `VerifyUserLicense` 、 `GetLicenseKey` 和 `VerifyLicenseKey` 被声明为控件工厂类的虚拟成员函数，因此您可以自定义控件的授权行为。

例如，可以通过重写 `VerifyUserLicense` 或成员函数为控件提供多个级别的授权 `VerifyLicenseKey` 。 在此函数中，可以根据检测到的许可证级别调整向用户公开的属性或方法。

你还可以将代码添加到 `VerifyLicenseKey` 函数，该函数提供自定义方法以通知用户控件创建已失败。 例如，在 `VerifyLicenseKey` 成员函数中，您可以显示一个消息框，指出控件未能初始化和原因。

> [!NOTE]
> 自定义 ActiveX 控件许可证验证的另一种方法是，检查注册数据库中是否有特定的注册表项，而不是调用 `AfxVerifyLicFile` 。 有关默认实现的示例，请参阅本文的[实现文件修改](#_core_implementation_file_modifications)部分。

有关许可问题的其他讨论，请参阅[升级现有 ActiveX 控件](upgrading-an-existing-activex-control.md)中的许可问题。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[MFC ActiveX 控件向导](reference/mfc-activex-control-wizard.md)
