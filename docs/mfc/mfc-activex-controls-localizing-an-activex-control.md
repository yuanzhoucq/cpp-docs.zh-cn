---
title: MFC ActiveX 控件： 本地化 ActiveX 控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9a6495c23695f8cdedf45fbdd7cbc915b96873e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929603"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>MFC ActiveX 控件：本地化 ActiveX 控件
本文讨论本地化 ActiveX 控件接口的过程。  
  
 如果您要使 ActiveX 控件适应于国际市场，则可能需要本地化控件。 Windows 支持默认英语之外的许多语言，包括德语、法语和瑞典语。 如果控件的接口只显示英文，则这可能会给控件带来问题。  
  
 通常，ActiveX 控件应始终将其区域设置基于环境 LocaleID 属性。 有三种方法可以实现此操作：  
  
-   始终按需基于环境 LocaleID 属性的当前值加载资源。 MFC ActiveX 控件示例[LOCALIZE](../visual-cpp-samples.md)使用此策略。  
  
-   在实例化第一个控件时基于环境 LocaleID 属性加载资源，并将这些资源用于所有其他实例。 本文演示此策略。  
  
    > [!NOTE]
    >  如果将来的实例具有不同的区域设置，则这在某些情况下不会正常运行。  
  
-   使用`OnAmbientChanged`通知函数以动态方式加载容器的区域设置的正确资源。  
  
    > [!NOTE]
    >  这对控件有效，但运行时 DLL 将不能在环境 LocaleID 属性更改时动态更新其自己的资源。 此外，ActiveX 控件的运行时 DLL 将使用线程区域设置确定其资源的区域设置。  
  
 本文其余部分介绍两个本地化策略。 第一个策略[本地化控件的可编程性接口](#_core_localizing_your_control.92.s_programmability_interface)（属性、 方法和事件的名称）。 第二个策略[本地化控件的用户界面](#_core_localizing_the_control.92.s_user_interface)，使用容器的环境 LocaleID 属性。 有关控件本地化的演示，请参阅 MFC ActiveX 控件示例[LOCALIZE](../visual-cpp-samples.md)。  
  
##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> 本地化控件的可编程性接口  
 在本地化控件的可编程性接口（编写使用控件的应用程序的程序员使用的接口），您必须为要支持的每种语言创建一个修改版本的控件 .IDL 文件（用于生成控件类型库的脚本）。 这是您需要本地化控件属性名的唯一位置。  
  
 当您开发一个本地化控件时，在类型库级别包括区域设置 ID 作为特性。 例如，如果要提供一个包含法语本地化属性名称的类型库，请制作 SAMPLE.IDL 文件的副本，称它为 SAMPLEFR.IDL。 将区域设置 ID 特性添加到文件（法语的区域设置 ID 为 0x040c），如下所示：  
  
 [!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]  
  
 将 SAMPLEFR.IDL 中的属性名更改为其法语等效项，然后使用 MKTYPLIB.EXE 生成法语类型库 SAMPLEFR.TLB。  
  
 若要创建多个本地化类型库，则可以将任何本地化 .IDL 文件添加到项目中，它们将会自动生成。  
  
#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>将 .IDL 文件添加到 ActiveX 控件项目  
  
1.  打开，请在你控件项目**项目**菜单上，单击**添加现有项**。  
  
     **添加现有项**对话框随即出现。  
  
2.  如果需要，选择要查看的驱动器和目录。  
  
3.  在**文件类型**框中，选择**所有文件 (\*。\*)**.  
  
4.  在文件列表框中，双击要插入项目的 .IDL 文件。  
  
5.  单击**打开**在你已添加所有必要。IDL 文件。  
  
 由于文件已添加到项目中，因此它们将在剩下的项目生成后生成。 本地化类型库位于当前 ActiveX 控件项目目录中。  
  
 在代码内，将始终使用并且绝不本地化内部属性名称（通常为英语）。 这包括控件调度属性、调度交换函数和属性页数据交换代码。  
  
 只有一个类型库 (.TLB) 文件可绑定到控件实现 (.OCX) 文件的资源。 这通常是使用标准化（通常为英语）名称的版本。 若要推出控件的本地化版本，则需要针对适当的区域设置推出 .OCX（其已绑定到默认 .TLB 版本）和 .TLB。 这意味着仅英语版本需要 .OCX，因为正确的 .TLB 已绑定到它。 对于其他区域设置，本地化类型库还必须与 .OCX 一起推出。  
  
 若要确保控件的客户可以找到本地化的类型库，请在 Windows 系统注册表的 TypeLib 部分下注册区域设置特定的 .TLB 文件。 第三个参数 （一般可选） 的[AfxOleRegisterTypeLib](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib)函数提供为此目的。 以下示例为 ActiveX 控件注册一个法语类型库：  
  
 [!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]  
  
 注册控件时，`AfxOleRegisterTypeLib` 函数将在与控件相同的目录中查找指定 .TLB 文件，并在 Windows 注册数据库中注册该文件。 如果未找到 .TLB 文件，则函数将没有任何效果。  
  
##  <a name="_core_localizing_the_control.92.s_user_interface"></a> 本地化控件的用户界面  
 若要本地化控件的用户界面，请将所有控件的用户可见资源（如属性页和错误消息）放入语言特定资源 DLL 中。 然后您可以使用容器的环境 LocaleID 属性为用户的区域设置选择适当的 DLL。  
  
 以下代码示例演示一种为特定区域设置查找和加载资源 DLL 的方法。 此示例称为 `GetLocalizedResourceHandle` 的成员函数可能是 ActiveX 控件类的成员函数：  
  
 [!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]  
  
 请注意，可以在 switch 语句的每个 case 中检查子语言 ID，以提供更专用的本地化。 此函数的演示，请参阅`GetResourceHandle`函数在 MFC ActiveX 控件示例[LOCALIZE](../visual-cpp-samples.md)。  
  
 当控件先将自身加载到一个容器时，它可以调用[colecontrol:: Ambientlocaleid](../mfc/reference/colecontrol-class.md#ambientlocaleid)以检索区域设置 id。 控件之后可以将返回的区域设置 ID 值传递到 `GetLocalizedResourceHandle` 函数，这将加载合适的资源库。 控件应传递生成的句柄，如果有的话，到[AfxSetResourceHandle](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):  
  
 [!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]  
  
 将上面的代码示例放入该控件，如的重写的成员函数[colecontrol:: Onsetclientsite](../mfc/reference/colecontrol-class.md#onsetclientsite)。 此外， *m_hResDLL*应控件类的成员变量。  
  
 您可以使用类似的逻辑本地化控件的属性页。 若要本地化属性页，请将类似于下面的示例代码添加到属性页的实现文件 (的重写中[COlePropertyPage::OnSetPageSite](../mfc/reference/colepropertypage-class.md#onsetpagesite)):  
  
 [!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

