---
title: MFC ActiveX 控件： 许可 ActiveX 控件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
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
ms.openlocfilehash: 115cddbda3323ee3c6450bc30f0a959c346c5d72
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535245"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC ActiveX 控件：许可 ActiveX 控件
许可支持，ActiveX 控件的可选功能允许你控制能够使用或分发该控件。 (的许可问题的更多讨论，请参阅中的许可问题[升级现有 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)。)  

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 本文将取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。
  
 本文讨论以下主题：  
  
-   [许可的 ActiveX 控件概述](#_core_overview_of_activex_control_licensing)  
  
-   [创建一个授权的控件](#_core_creating_a_licensed_control)  
  
-   [许可支持](#_core_licensing_support)  
  
-   [自定义 ActiveX 控件的许可](#_core_customizing_the_licensing_of_an_activex_control)  
  
 实现许可的 ActiveX 控件允许您，作为控件开发人员，以确定其他人如何使用 ActiveX 控件。 与该控件提供控件购买者和。许可证文件，与购买者但不是可能分发控件，该协议。许可证文件，使用该控件的应用程序。 这可以防止从编写新应用程序使用而无需第一个许可从您的控件的控件，该应用程序的用户。  
  
##  <a name="_core_overview_of_activex_control_licensing"></a> 许可的 ActiveX 控件概述  
 若要为 ActiveX 控件提供许可支持[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)类提供有关中的若干函数实现`IClassFactory2`接口： `IClassFactory2::RequestLicKey`， `IClassFactory2::GetLicInfo`，和`IClassFactory2::CreateInstanceLic`。 当容器应用程序开发人员发出请求以创建控件，调用的实例`GetLicInfo`进行验证的控件。许可证文件存在。 如果控件授予许可，可以创建控件的实例，并将其放置在容器中。 开发人员完成构造容器应用程序后，另一个函数调用，这一次`RequestLicKey`，进行。 此函数返回到容器应用程序的许可证密钥 （简单的字符字符串）。 然后将其返回的键嵌入在应用程序中。  
  
 下图演示将容器应用程序的开发期间使用的 ActiveX 控件的许可证验证。 正如前面提到，容器应用程序开发人员必须具有适当。若要创建的控件实例的开发计算机上安装的许可证文件。  
  
 ![授权 ActiveX 控件开发时验证了已](../mfc/media/vc374d1.gif "vc374d1")  
开发期间授权 ActiveX 控件的验证  
  
 当最终用户运行容器应用程序时，将出现下图中所示的下一步过程。  
  
 当启动应用程序时，控件的实例通常需要创建。 通过进行调用，容器就可以完成此`CreateInstanceLic`，将嵌入的许可证密钥作为参数传递。 然后嵌入的许可证密钥和许可证密钥的控件的副本之间进行字符串比较。 如果匹配成功，则创建控件的实例和应用程序将继续正常执行。 请注意，。许可证文件不需要控制用户的计算机上存在。  
  
 ![授权 ActiveX 控件时执行验证了已](../mfc/media/vc374d2.gif "vc374d2")  
执行期间授权 ActiveX 控件的验证  
  
 控件授权包含两个基本组件： 控件实现 DLL 中的特定代码和许可证文件。 代码组成两个 （或可能是三个） 函数调用和字符串，简称为"许可证"，包含字符串的版权声明。 控件实现中找到这些调用和许可字符串 (。CPP) 文件。 ActiveX 控件向导，生成的许可证文件是具有版权的语句的文本文件。 它名为使用与项目名称。公有扩展，例如示例。许可证。 授权的控件必须带有许可证文件根据需要设计时使用。  
  
##  <a name="_core_creating_a_licensed_control"></a> 创建一个授权的控件  
 当你使用 ActiveX 控件向导创建控制框架时，很容易包括许可支持。 当您指定控件应具有的运行时许可证时，ActiveX 控件向导将代码添加到控件类以支持授权。 代码包含的函数的使用许可证验证密钥和许可证文件。 此外可以修改这些函数以自定义控件授权。 有关许可证自定义项的详细信息，请参阅[自定义 ActiveX 控件的许可](#_core_customizing_the_licensing_of_an_activex_control)这篇文章中更高版本。  
  
#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>若要添加对许可 ActiveX 控件向导创建控件项目时的支持  
  
1.  使用中的说明[创建 MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)。 **应用程序设置**ActiveX 控件向导页包含用于创建控件的运行时许可证的选项。  
  
 ActiveX 控件向导现在会生成一种 ActiveX 控件框架，包括基本授权支持。 授权代码的详细说明，请参阅下一主题。  
  
##  <a name="_core_licensing_support"></a> 许可支持  
 使用 ActiveX 控件向导将许可支持添加到 ActiveX 控件，ActiveX 控件向导会添加声明并实现的许可功能的代码添加到控制标头和实现文件。 此代码组成`VerifyUserLicense`成员函数和一个`GetLicenseKey`成员函数，重写中找到的默认实现[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) 。 这些函数检索，并确认控制许可证。  
  
> [!NOTE]
>  第三个成员函数，`VerifyLicenseKey`不生成 ActiveX 控件向导，但可以重写以自定义许可证密钥验证行为。  
  
 这些成员函数是：  
  
-   [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)  
  
     验证控件，允许通过检查系统中存在控制许可证文件的设计时使用情况。 在处理过程由框架调用此函数`IClassFactory2::GetLicInfo`和`IClassFactory::CreateInstanceLic`。  
  
-   [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)  
  
     从控件 DLL 请求的唯一键。 此密钥是嵌入在容器应用程序中，与结合使用更高版本， `VerifyLicenseKey`，以创建控件的实例。 在处理过程由框架调用此函数`IClassFactory2::RequestLicKey`。  
  
-   [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)  
  
     验证嵌入的键和控件的唯一键相同。 这样，要创建的供其使用的控件实例的容器。 在处理过程由框架调用此函数`IClassFactory2::CreateInstanceLic`，可以重写为自定义的验证的许可证密钥。 默认实现将执行字符串比较。 有关详细信息，请参阅[自定义 ActiveX 控件的许可](#_core_customizing_the_licensing_of_an_activex_control)，这篇文章中更高版本。  
  
###  <a name="_core_header_file_modifications"></a> 标头文件修改  
 ActiveX 控件向导将以下代码放在控件头文件中。 在此示例中，两个成员函数`CSampleCtrl`的对象`factory`声明的另一个验证控件是否存在。许可证文件，另一个用于检索要在包含该控件的应用程序中使用的许可证密钥：  
  
 [!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]  
  
###  <a name="_core_implementation_file_modifications"></a> 实现文件修改  
 ActiveX 控件向导控件实现文件声明许可证文件名和许可字符串中放置以下两个语句：  
  
 [!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]  
  
> [!NOTE]
>  如果您修改`szLicString`以任何方式，还必须修改该控件中的第一行。许可证文件或许可将无法正常工作。  
  
 ActiveX 控件向导将以下代码放置在控件实现文件来定义控件类的`VerifyUserLicense`和`GetLicenseKey`函数：  
  
 [!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]  
  
 最后， **ActiveX 控件向导**修改控件项目。IDL 文件。 **许可**关键字已添加到该控件，如以下示例所示的组件类声明：  
  
 [!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]  
  
##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> 自定义 ActiveX 控件的许可  
 因为`VerifyUserLicense`， `GetLicenseKey`，和`VerifyLicenseKey`声明作为控件工厂类的虚拟成员函数可以自定义控件的授权行为。  
  
 例如，你可以提供多个级别的授权控件通过重写`VerifyUserLicense`或`VerifyLicenseKey`成员函数。 在此函数可以调整到根据你检测到的许可证级别用户公开的属性或方法。  
  
 此外可以添加到代码`VerifyLicenseKey`提供自定义的方法，通知用户控制创建失败的函数。 例如，在你`VerifyLicenseKey`成员函数可以显示消息框指出控件无法初始化和原因。  
  
> [!NOTE]
>  自定义 ActiveX 控件许可证验证另一种方法是检查注册数据库的特定注册表项，而不是调用`AfxVerifyLicFile`。 默认实现的示例，请参阅[实现文件修改](#_core_implementation_file_modifications)本文的部分。  
  
 许可问题的更多讨论，请参阅中的许可问题[升级现有 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)

