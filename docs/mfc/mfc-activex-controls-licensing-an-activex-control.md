---
title: "MFC ActiveX 控件：许可 ActiveX 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COleObjectFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleObjectFactory 类, 授权控件"
  - "GetLicenseKey 方法"
  - "授权 ActiveX 控件"
  - "MFC ActiveX 控件, 授权"
  - "VerifyLicenseKey 方法"
  - "VerifyUserLicense 方法"
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：许可 ActiveX 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持允许，ActiveX 控件可选功能，允许您控制谁可以使用或分布控件。\(对于本发行许可证的讨论，请参见 [升级现有的 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)许可证的颁发。\)  
  
 本文讨论以下主题：  
  
-   [概述使用 ActiveX 控件](#_core_overview_of_activex_control_licensing)  
  
-   [创建将一个授权控件](#_core_creating_a_licensed_control)  
  
-   [授权支持](#_core_licensing_support)  
  
-   [自定义 ActiveX 控件的授权](#_core_customizing_the_licensing_of_an_activex_control)  
  
 实现授权的 ActiveX 控件，可以为控件开发，确定其他人员如何使用 ActiveX 控件。  购买者控件可以提供与控件和名为 .LIC 文件，使用协议购买者可能分布控件，但是，不是名为 .LIC 文件，包含使用控件的应用程序。  这防止该应用程序的用户而编写使用控件的新应用程序，而第一个没有，则从授权的控件。  
  
##  <a name="_core_overview_of_activex_control_licensing"></a> 概述使用 ActiveX 控件  
 为 ActiveX 控件需要提供授权支持 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) 类，为 **IClassFactory2** 接口的提供了一些函数实现：**IClassFactory2::RequestLicKey**、**IClassFactory2::GetLicInfo**和 **IClassFactory2::CreateInstanceLic**。  在容器应用程序开发人员发出请求创建控件的实例时，对 `GetLicInfo` 的一次调用验证控件名为 .LIC 文件存在。  如果控件被允许，控件实例在容器中创建和设置。  在开发人员实现构造容器应用程序后，其他函数调用，则 `RequestLicKey`的此次，调用。  此函数返回许可证秘钥 \(简单的字符串\) 访问容器应用程序。  返回的键。应用程序随后嵌入。  
  
 下图演示在容器应用程序的开发过程，则将 ActiveX 控件的许可证验证。  如上所述，容器应用程序开发人员必须在开发计算机安装相应的文件名为 .LIC 创建控件的实例。  
  
 ![开发时验证了已获许可的 ActiveX 控件](../mfc/media/vc374d1.png "vc374D1")  
开发期间授权 ActiveX 控件的验证  
  
 如果最终用户在容器应用程序，显示下进程，在下图上，发生。  
  
 当应用程序开始，通常控件所需的实例。  容器通过调用完成为 `CreateInstanceLic`，后者传递嵌入的许可证密钥作为参数。  字符串比较然后可以在嵌入的许可证许可证秘钥的键和控件的副本之间。  如果匹配成功，创建控件的实例，并且应用程序将继续正常执行。  请注意名为 .LIC 文件不必位于控件用户的计算机。  
  
 ![执行时验证了已获许可的 ActiveX 控件](../mfc/media/vc374d2.png "vc374D2")  
执行期间授权 ActiveX 控件的验证  
  
 控件授权由两种基本的组件：在控件实现 DLL 的特定代码和许可证文件。  代码由两个或三个 \(可能\) 函数调用和字符串，此后称为“许可证”，字符串包含用于版权声明。  这些调用和许可证字符串在控件的实现 \(.cpp\) 文件中。  许可证文件，生成的 ActiveX 控件向导，是与版权语句的文本文件。  使用扩展名为 .LIC，名为，例如 SAMPLE.LIC 的项目名称。  如果使用设计时是必需的，必须由许可证文件附带一个授权控件。  
  
##  <a name="_core_creating_a_licensed_control"></a> 创建将一个授权控件  
 在将 ActiveX 控件向导创建控件框架时，很容易对包含授权支持。  当您指定时控件应当具有一个运行时许可证，ActiveX 控件向导添加代码到控件类。支持授权。  代码包含对验证许可证使用一个键和许可证文件的函数。  也可以修改这些函数自定义控件授权。  有关允许自定义项的更多信息，请参见 [自定义 ActiveX 控件的授权](#_core_customizing_the_licensing_of_an_activex_control) 本文后面。  
  
#### 添加允许且支持 ActiveX 控件向导，则可以在创建控件项目  
  
1.  使用指令。[创建 MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)。  页 **应用程序设置** ActiveX 控件向导包含选项创建一个运行时许可证的控件。  
  
 ActiveX 控件向导现在生成包含基的授权支持的 ActiveX 控件框架。  有关启用代码的更详细解释，请参见下面的主题。  
  
##  <a name="_core_licensing_support"></a> 授权支持  
 在将 ActiveX 控件向导添加授权支持到 ActiveX 控件时，ActiveX 控件向导添加声明的代码，并实现授权功能添加到控件标头和实现文件。  本代码编写 `VerifyUserLicense` 成员函数和 `GetLicenseKey` 成员函数，会重写在 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) 中的默认实现。  这些函数检索并验证控件许可证。  
  
> [!NOTE]
>  第三，`VerifyLicenseKey` 成员函数未由向导生成的 ActiveX 控件，可以重写，但是自定义许可证密钥验证行为。  
  
 这些成员函数无效：  
  
-   [VerifyUserLicense](../Topic/COleObjectFactory::VerifyUserLicense.md)  
  
     验证控件通过检查控件许可证文件存在的系统使设计时使用。  作为处理 **IClassFactory2::GetLicInfo** 和 **IClassFactory::CreateInstanceLic**的一部分，此函数由框架调用。  
  
-   [GetLicenseKey](../Topic/COleObjectFactory::GetLicenseKey.md)  
  
     请求控件 DLL 的唯一键。  此密钥在容器应用程序嵌入并与 `VerifyLicenseKey`结合使用以后用于，在中，创建控件的实例。  作为处理 **IClassFactory2::RequestLicKey**的一部分，此函数由框架调用。  
  
-   [VerifyLicenseKey](../Topic/COleObjectFactory::VerifyLicenseKey.md)  
  
     验证嵌入的键和控件的唯一键相同。  这样容器创建控件的实例。它的使用。  此函数由框架调用作为处理 **IClassFactory2::CreateInstanceLic** 的一部分，可提供重写许可证秘钥的自定义的验证。  默认实现均执行字符串比较。  有关更多信息，请参见 [自定义 ActiveX 控件的授权](#_core_customizing_the_licensing_of_an_activex_control)，本文后面。  
  
###  <a name="_core_header_file_modifications"></a> 修改头文件  
 ActiveX 控件向导控件中头文件中以下代码。  在本示例中，`CSampleCtrl` 对象 `factory` 的两个成员函数声明中，验证控件名为 .LIC 文件存在用于检索应用程序的许可证秘钥控件包含一个和一个：  
  
 [!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_1.h)]  
  
###  <a name="_core_implementation_file_modifications"></a> 实现文件修改  
 ActiveX 控件向导在控件的实现文件中以下两个语句都声明允许文件名和许可证字符串：  
  
 [!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_2.cpp)]  
  
> [!NOTE]
>  如果您修改使用 **szLicString**，则还必须修改控件名为 .LIC 文件的第一行或授权不能正常工作。  
  
 ActiveX 控件向导在控件的实现文件放置以下代码来定义控件类的 `VerifyUserLicense` 和 `GetLicenseKey` 函数：  
  
 [!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_3.cpp)]  
  
 最后，修改 **ActiveX Control Wizard** 控件项目的 .idl 文件。  **licensed** 关键字添加到控件的 Coclass 声明，如下例所示：  
  
 [!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_4.idl)]  
  
##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> 自定义 ActiveX 控件的授权  
 因为 `VerifyUserLicense`、`GetLicenseKey`和 `VerifyLicenseKey` 声明虚函数，当控件工厂类的成员，则可以自定义控件的授权行为。  
  
 例如，您可以为控件提供的多种级别的授权通过重写 `VerifyUserLicense` 或 `VerifyLicenseKey` 成员函数。  在此函数中可以调整的属性或方法向用户根据您检测的许可级别。  
  
 还可以将代码添加通知为用户提供自定义的方式控制创建失败的 `VerifyLicenseKey` 函数。  例如，`VerifyLicenseKey` 成员函数可以显示一个消息框，指出控件未能初始化，以及原因。  
  
> [!NOTE]
>  另一个方式自定义 ActiveX 控件许可证验证将检查特定的注册表项注册数据库，而不是调用 `AfxVerifyLicFile`。  有关默认实现的示例，请参见本文的 [实现文件修改](#_core_implementation_file_modifications) 一节。  
  
 讨论有关许可发布的讨论，请参见 [升级现有的 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)许可证的颁发。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)