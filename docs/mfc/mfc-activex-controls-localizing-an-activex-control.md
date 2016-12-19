---
title: "MFC ActiveX 控件：本地化 ActiveX 控件 | Microsoft Docs"
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
  - "LocaleID"
  - "AfxOleRegisterTypeLib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LocaleID ambient 属性"
  - "本地化, ActiveX 控件"
  - "LOCALIZE 示例 [MFC]"
  - "MFC ActiveX 控件, 本地化"
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：本地化 ActiveX 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文讨论本地化的 ActiveX 控件接口方法。  
  
 如果您想要为 ActiveX 控件的一种国际市场，可能需要本地化控件。  除了默认英语，包括、、法语和瑞典语，窗口支持多种语言。  如果其接口只，在英语控件便可能存在的问题。  
  
 通常，ActiveX 控件总是应基于其区域设置 LocaleID 环境属性。  有三种方法可以实现此操作：  
  
-   加载资源，始终按需，基于环境 LocaleID 属性的当前值。  MFC ActiveX 工具控件使用此策略。[本地化](../top/visual-cpp-samples.md)  
  
-   在第一个控件 LocaleID 基于环境属性是实例，并且，对于其他实例时，使用这些资源不加载资源。  本文演示此策略。  
  
    > [!NOTE]
    >  如果将来的实例具有不同区域设置，这在某些情况下不会正确工作。  
  
-   使用 **OnAmbientChanged** 函数通知动态加载容器的区域设置适当的资源。  
  
    > [!NOTE]
    >  这对控件是有效，但运行时，DLL 将无法动态地更新其特定资源，在环境 LocaleID 属性更改。  此外，ActiveX 控件的运行时程 DLL 使用线程区域设置决定对其资源的区域设置。  
  
 本文的其余部分将介绍两本地化的策略。  第一种策略 [本地化控件的可编程接口](#_core_localizing_your_control.92.s_programmability_interface) \(属性、方法和事件的名称。\)  使用容器的环境 LocaleID 属性的第二个策略，[本地化控件的用户界面](#_core_localizing_the_control.92.s_user_interface)。  有关控件的本地化演示，请参见 [本地化](../top/visual-cpp-samples.md)。工具 MFC ActiveX 控件  
  
##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> 本地化控件的可编程接口  
 在本地化控件的可编程接口 \(使用接口的程序员编写使用控件\) 的应用程序时，必须在控件 \(.idl 文件生成的控件类型的脚本库\) 修改生成每种要支持的语言。  这是需要本地化控件属性名的位置。  
  
 当您开发一个本地化的控件，包括区域设置 ID 为在类型库级别的特性。  例如，在中，如果要提供类型库以法语本地化的属性名称，请将复制 SAMPLE.IDL 文件，并将它 SAMPLEFR.IDL。  添加区域设置 ID 特性。文件 \(法语的区域设置 ID 0x040c 为\)，如下所示：  
  
 [!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_1.idl)]  
  
 将 SAMPLEFR.IDL 的属性命名为其等效的法语，然后使用 MKTYPLIB.EXE 生产法国类型库，SAMPLEFR.TLB。  
  
 若要创建多个本地化的类型库可以将所有本地化的 .idl 文件添加到项目，并会自动生成。  
  
#### 将.IDL file添加到 MFC ActiveX 控件项目  
  
1.  使控制项目打开，在**Project** 菜单，单击 **Add Existing Item**。  
  
     将出现**“添加现有项”**对话框。  
  
2.  如果需要，选择驱动器和目录所示。  
  
3.  在**“文件类型”**框中，选择**“所有文件\(\*.\*\)”**。  
  
4.  在文件列表框中，双击要插入到项目的 .idl 文件。  
  
5.  在添加了所有必需的 .idl 文件时，单击 **打开**。  
  
 由于文件添加到项目中，则将生成，在项目的其余生成。  本地化的类型库。当前 ActiveX 控件项目目录中。  
  
 在代码内 \(通常，在英语\) 始终使用内部属性名而决不本地化。  这包括控件映射属性，调度交换函数和属性页数据交换的代码。  
  
 只有一类型库 \(.tlb\) 文件能绑定到控件 \(实现 .ocx\) 文件中。  这通常与的标准化 \(通常，英语\) 名称的版本。  交付您需要支持 .ocx \(已绑定到的默认版本 .tlb\) 控件的本地化版本和相应的 .tlb 的区域设置。  这意味着只 .ocx 为英文版是必需的，因为正确的 .tlb 已绑定到它。  对于其他区域设置，还必须使用本地化的类型库。.ocx。  
  
 若要确保控件的客户可以找到本地化的类型库，请注册区域设置特定的 .tlb 文件的 Windows 系统注册表的 TypeLib 节下面。  为此提供第三个形参 \(通常可选\) [AfxOleRegisterTypeLib](../Topic/AfxOleRegisterTypeLib.md) 函数。  下面的示例注册 ActiveX 控件的、类型库：  
  
 [!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_2.cpp)]  
  
 当控件注册时，`AfxOleRegisterTypeLib` 函数会自动找到目录中指定的 .tlb 文件与控件相同并注册它在 Windows 注册数据库。  如果 .tlb 文件未找到，函数不起作用。  
  
##  <a name="_core_localizing_the_control.92.s_user_interface"></a> 本地化控件的用户界面  
 若要本地化控件的用户界面，请将所有控件的用户可见的资源 \(例如页属性和错误消息\) 为特定语言的资源 DLL。  然后可以使用容器的环境 LocaleID 属性选择用户的区域设置进行相应的 DLL。  
  
 下面的代码示例演示一种方法定位和加载特定区域设置的资源 DLL。  此成员函数，调用该示例的 `GetLocalizedResourceHandle`，可以为 ActiveX 控件类的成员函数：  
  
 [!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_3.cpp)]  
  
 注意子语言 ID 能签入开关语句中每种情况，提供专用的本地化。  有关此函数的用途，请参见在 MFC ActiveX 工具控件示例 [本地化](../top/visual-cpp-samples.md)的 `GetResourceHandle` 函数。  
  
 在控件第一个将其本身加载到容器时，它可以调用 [COleControl::AmbientLocaleID](../Topic/COleControl::AmbientLocaleID.md) 检索区域设置 ID.  控件可以将返回的区域设置 ID 的值传递到 `GetLocalizedResourceHandle` 函数，加载合适的资源库。  控件应将生成的处理，如果存在，到 [AfxSetResourceHandle](../Topic/AfxSetResourceHandle.md):  
  
 [!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_4.cpp)]  
  
 将上面代码示例为控件的成员函数，例如 [COleControl::OnSetClientSite](../Topic/COleControl::OnSetClientSite.md)重写。  此外，`m_hResDLL` 应该是控件类中的成员变量。  
  
 可以为本地化控件的属性页使用类似的逻辑。  若要本地化属性页，请添加代码类似于下面的示例。实现属性页 \(文件在 [COlePropertyPage::OnSetPageSite](../Topic/COlePropertyPage::OnSetPageSite.md)重写\):  
  
 [!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_5.cpp)]  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)