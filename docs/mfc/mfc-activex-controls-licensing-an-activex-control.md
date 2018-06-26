---
title: MFC ActiveX 控件： 许可 ActiveX 控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COleObjectFactory
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0b1e8f0c54cf4d409aedb99fc3195b927d5f127
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929739"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC ActiveX 控件：许可 ActiveX 控件
许可支持，ActiveX 控件的一个可选功能允许你控制能够使用或分发该控件。 (的许可问题的更多讨论，请参阅中的授权问题[升级现有 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)。)  
  
 本文讨论以下主题：  
  
-   [授权的 ActiveX 控件概述](#_core_overview_of_activex_control_licensing)  
  
-   [创建授权的控件](#_core_creating_a_licensed_control)  
  
-   [许可支持](#_core_licensing_support)  
  
-   [自定义授权 ActiveX 控件](#_core_customizing_the_licensing_of_an_activex_control)  
  
 实现授权的 ActiveX 控件允许您，作为控件开发人员，以确定其他人使用 ActiveX 控件的方式。 与该控件提供控件购买者和。许可证文件，与购买者可以但不是发布该控件，该协议。具有使用控件的应用程序的许可证文件。 这样可以防止编写新的应用程序无需第一个授权控件从你使用的控件，该应用程序的用户。  
  
##  <a name="_core_overview_of_activex_control_licensing"></a> 授权的 ActiveX 控件概述  
 为 ActiveX 控件，提供许可支持[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)类提供多个函数的实现`IClassFactory2`接口： `IClassFactory2::RequestLicKey`， `IClassFactory2::GetLicInfo`，和`IClassFactory2::CreateInstanceLic`。 当容器应用程序开发人员发出请求以创建该控件，调用的实例`GetLicInfo`进行验证的控件。许可证文件存在。 如果控件授予许可，则可以创建控件的实例，并将其放在容器中。 开发人员已完成构造容器应用程序后，另一个函数调用，此时间`RequestLicKey`，进行。 此函数将返回到容器应用程序的许可密钥 （简单字符字符串）。 然后将其应用程序中嵌入则返回的键。  
  
 下图演示在容器应用程序的开发期间将使用的 ActiveX 控件的许可证验证。 如前所述，容器应用程序开发人员必须已将正确。若要创建的控件实例的开发计算机上安装的许可证文件。  
  
 ![授权 ActiveX 控件开发时验证了已](../mfc/media/vc374d1.gif "vc374d1")  
开发期间授权 ActiveX 控件的验证  
  
 当最终用户运行的容器应用程序时下, 一步的过程中下, 图中中, 所示出现。  
  
 当启动应用程序时，控件的实例通常需要创建。 通过进行调用的容器完成此`CreateInstanceLic`，作为参数传递的嵌入的许可证密钥。 然后嵌入的许可证密钥和许可证密钥的控件的副本之间进行字符串比较。 如果匹配成功，则创建的控件实例和应用程序将继续正常执行。 请注意，。许可证文件不需要控制用户的计算机上存在。  
  
 ![授权 ActiveX 控件时执行验证了已](../mfc/media/vc374d2.gif "vc374d2")  
执行期间授权 ActiveX 控件的验证  
  
 控件授权包括两个基本组件： 在控件实现 DLL 中的特定代码和许可证文件。 代码组成两个 （或可能是三个） 的函数调用和字符字符串，简称为"许可证"，包含字符串的版权声明。 这些调用和许可证字符串位于控件实现 (。CPP) 文件。 ActiveX 控件向导，生成的许可证文件是具有版权语句的文本文件。 它将使用由项目名称和命名。许可证扩展，例如示例。许可证。 授权的控件必须附带由许可证文件，如果需要设计时使用。  
  
##  <a name="_core_creating_a_licensed_control"></a> 创建授权的控件  
 当你使用 ActiveX 控件向导创建控制框架时，很容易地包括许可支持。 当你指定的控件应具有运行时许可证时，ActiveX 控件向导会将代码添加到控件类，以支持授权。 代码包含的密钥和许可证文件用于许可证验证的函数。 此外可以修改这些函数以自定义控件授权。 有关许可证自定义项的详细信息，请参阅[自定义的 ActiveX 控件许可](#_core_customizing_the_licensing_of_an_activex_control)本文后续部分中。  
  
#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>若要添加为授权使用 ActiveX 控件向导创建控件项目时的支持  
  
1.  使用中的说明[创建 MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)。 **应用程序设置**ActiveX 控件向导的页面包含创建控件的运行时许可证的选项。  
  
 ActiveX 控件向导现在将生成一种 ActiveX 控件框架，包括基本授权的支持。 有关授权的代码的详细说明，请参阅下一主题。  
  
##  <a name="_core_licensing_support"></a> 许可支持  
 ActiveX 控件向导用于将授权的支持添加到 ActiveX 控件，则 ActiveX 控件向导会添加声明并实现授权的功能的代码添加到控制标头和实现文件。 此代码组成`VerifyUserLicense`成员函数和`GetLicenseKey`成员函数，其重写中找到的默认实现[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) 。 这些函数检索，并确认控件许可证。  
  
> [!NOTE]
>  第三个成员函数时，`VerifyLicenseKey`不生成 ActiveX 控件向导，但可以重写自定义的许可证密钥验证行为。  
  
 这些成员函数是：  
  
-   [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)  
  
     验证控件通过检查系统中存在的控件许可证文件的允许设计时使用。 处理过程中由框架调用此函数`IClassFactory2::GetLicInfo`和`IClassFactory::CreateInstanceLic`。  
  
-   [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)  
  
     从控件 DLL 请求的唯一键。 此密钥嵌入到容器应用程序，并结合使用更高版本， `VerifyLicenseKey`，若要创建的控件实例。 处理过程中由框架调用此函数`IClassFactory2::RequestLicKey`。  
  
-   [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)  
  
     验证嵌入的键和控件的唯一键相同。 这样，要创建它的使用控件的实例的容器。 处理过程中由框架调用此函数`IClassFactory2::CreateInstanceLic`并且可以重写提供的许可证密钥的自定义的验证。 默认实现将执行字符串比较。 有关详细信息，请参阅[自定义的 ActiveX 控件许可](#_core_customizing_the_licensing_of_an_activex_control)，本文稍后的。  
  
###  <a name="_core_header_file_modifications"></a> 标头文件修改  
 ActiveX 控件向导将下面的代码放在控件头文件。 在此示例中，两个成员函数的`CSampleCtrl`的对象`factory`声明，另一个验证控件的状态。许可证文件和另一个用于检索要在包含控件的应用程序中使用的许可证密钥：  
  
 [!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]  
  
###  <a name="_core_implementation_file_modifications"></a> 实现文件修改  
 ActiveX 控件向导将在控件实现文件来声明许可证文件名和许可字符串中的以下两个语句：  
  
 [!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]  
  
> [!NOTE]
>  如果你修改`szLicString`以任何方式，还必须修改控件中的第一行。许可证文件或授权将无法正常工作。  
  
 ActiveX 控件向导将以下代码放在控件实现文件中定义的控件类的`VerifyUserLicense`和`GetLicenseKey`函数：  
  
 [!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]  
  
 最后， **ActiveX 控件向导**修改控件项目。IDL 文件。 **许可**关键字已添加到该控件，如以下示例所示的组件类声明：  
  
 [!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]  
  
##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> 自定义授权 ActiveX 控件  
 因为`VerifyUserLicense`， `GetLicenseKey`，和`VerifyLicenseKey`被声明为控件工厂类的虚拟成员函数可以自定义控件的授权行为。  
  
 例如，你可以提供多个级别的授权控件，通过重写`VerifyUserLicense`或`VerifyLicenseKey`成员函数。 在此函数无法调整向你检测到的许可证级别根据用户公开的属性或方法。  
  
 你还可以添加到代码`VerifyLicenseKey`失败，通知控制创建的用户提供自定义的方法的函数。 例如，在你`VerifyLicenseKey`成员函数可以显示消息框中指出控件未能初始化和原因。  
  
> [!NOTE]
>  自定义 ActiveX 控件许可证验证另一种方法是检查特定的注册表项，而不是调用注册数据库`AfxVerifyLicFile`。 默认实现的示例，请参阅[实现文件修改](#_core_implementation_file_modifications)部分中的所述。  
  
 许可问题的更多讨论，请参阅中的授权问题[升级现有 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)

