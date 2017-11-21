---
title: "TN057: MFC 组件的本地化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.components
dev_langs: C++
helpviewer_keywords:
- components [MFC], localizing
- TN057
- resources [MFC], localization
- localization [MFC], MFC resources
- localization [MFC], MFC components
- MFC DLLs [MFC], localizing
- DLLs [MFC], localizing MFC
- localization [MFC], resources
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b8d8bcd21128b6d2d78d936e68f60040a75496c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="tn057-localization-of-mfc-components"></a>TN057：MFC 组件的本地化
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍了可用于本地化组件（如果它是应用程序或 OLE 控件或使用 MFC 的 DLL）的一些设计和过程。  
  
## <a name="overview"></a>概述  
 本地化使用 MFC 的组件时有两个真正要解决的问题。 首先，您必须本地化自己的资源 - 字符串、对话框和其他特定于组件的资源。 大多数使用 MFC 生成的组件也包含和使用 MFC 定义的很多资源。 您还必须提供本地化的 MFC 资源。 幸运的是，MFC 本身已提供了几种语言。  
  
 此外，您的组件应该为在其目标环境（欧洲语言环境或支持 DBCS 的环境）中运行做准备。 这主要取决于使用高位集正确地处理字符并使用双字节字符处理字符串的应用程序。 默认情况下，MFC 在这两种环境中处于启用状态，以便可以获得一个可在所有平台上使用并在设置时插入不同资源的单一全球二进制文件。  
  
## <a name="localizing-your-components-resources"></a>本地化组件的资源  
 本地化应用程序或 DLL 涉及将这些资源替换为与目标语言匹配的资源。 对于您自己的资源，此操作比较简单：在资源编辑器中编辑资源并生成您的应用程序。 如果你的代码编写正确将字符串或你希望本地化硬编码为 c + + 源代码的文本不所有本地化都可以只需通过修改资源。 事实上，你可以以某种方式实现你的组件，使它们都提供甚至不涉及生成原始代码的本地化版本。 这种方法更复杂，但很值得，并且这是为 MFC 本身选择的机制。 也可以通过将 EXE 或 DLL 文件加载到资源编辑器并直接编辑资源来本地化应用程序。 如有可能，每当您生成新版本的应用程序时，它都会要求重新应用那些更改。  
  
 避免这种情况的一个方法是在单独的 DLL（有时称为附属 DLL）中放置所有资源。 此 DLL 随后在运行时以动态方式加载，资源将从此 DLL 加载而不是从包含您的所有代码的主模块加载。 MFC 直接支持此方法。 请考虑一个名为 MYAPP.EXE 的应用程序；它可以将所有资源放在一个名为 MYRES.DLL 的 DLL 中。 在应用程序的 `InitInstance` 中，它将执行以下代码以加载该 DLL 并使 MFC 从该位置加载资源：  
  
```  
CMyApp::InitInstance()  
{ *// one of the first things in the init code  
    HINSTANCE hInst = LoadLibrary("myres.dll");

    if (hInst != NULL)  
    AfxSetResourceHandle(hInst);

 *// other initialization code would follow  
 .  
 .  
 .  
}  
```  
  
 从那以后，MFC 将从该 DLL 而非 myapp.exe 加载资源。 但是，所有资源都必须存在于该 DLL 中；MFC 不会搜索应用程序的实例来寻找给定的资源。 此方法适用于同样常规 MFC Dll 以及 OLE 控件。 您的安装程序将根据用户想采用的资源区域设置复制相应版本的 MYRES.DLL。  
  
 创建纯资源 DLL 相对简单一些。 您创建 DLL 项目，向其添加 .RC 文件，然后添加必需的资源。 如果您有不使用此方法的现有项目，则可以从该项目中复制资源。 将资源文件添加到项目后，你差不多已做好生成项目的准备。 必须执行唯一操作是设置链接器选项以包括**/NOENTRY**。 这将通知链接器，该 DLL 没有入口点-因为它没有代码，它具有不到入口点。  
  
> [!NOTE]
>  Visual C++ 4.0 和更高版本中的资源编辑器通过 .RC 文件支持多种语言。 这使您在单个项目中管理本地化很容易。 每种语言的资源由资源编辑器生成的预处理器指令控制。  
  
## <a name="using-the-provided-mfc-localized-resources"></a>使用提供的 MFC 本地化资源  
 您生成的任何 MFC 应用程序都会重复使用 MFC 中的两个内容：代码和资源。 也就是说，MFC 有各种错误消息、内置对话框以及 MFC 类使用的其他资源。 若要完全本地化应用程序，您不仅需要本地化应用程序的资源，还需要本地化直接来自 MFC 的资源。 MFC 自动提供了很多不同语言的资源文件，这样，当您面向的语言是 MFC 已支持的语言之一时，您只需确保使用这些本地化资源即可。  
  
 到本文撰写之时为止，MFC 支持中文、德语、西班牙语、法语、意大利语、日语和朝鲜语。 包含这些本地化版本的文件位于 MFC\INCLUDE\L.*（“L”表示已本地化）目录中。 例如，德语位于 MFC\INCLUDE\L.DEU 中。 若要使应用程序而不是位于 MFC\INCLUDE 中的文件中使用这些 RC 文件，添加`/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU`到 RC 的命令行 （这是只是一个示例; 你将需要进行替换你的选择，以及在其中安装了 Visual C 的目录的区域设置++).  
  
 如果应用程序以静态方式与 MFC 链接，以上指令将有效。 大多数应用程序以动态方式进行链接（因为这是 AppWizard 的默认设置）。 在此方案中，不仅代码以动态方式链接的资源也是如此。 因此，您可以在应用程序中本地化资源，但 MFC 实现资源仍将从 MFC7x.DLL（或更高版本）加载或从 MFC7xLOC.DLL（如果存在）加载。 您可以从两个不同的角度达到此目的。  
  
 更复杂的方法是附带本地化的 MFC7xLOC.DLL（如 MFC7xDEU 用于德语、MFC7xESP.DLL 用于西班牙语，等等）或更高版本之一，并在用户安装您的应用程序时将相应的 MFC7xLOC.DLL 安装到系统目录中。 这对于开发人员和最终用户可能非常复杂，因此不建议采用。 请参阅[技术说明 56](../mfc/tn056-installation-of-localized-mfc-components.md)有关此技术和及其告诫的详细信息。  
  
 最简单最安全的方法是将本地化的 MFC 资源包含在您的应用程序或 DLL 本身（或其附属 DLL，如果正在使用）中。 这将恰当地避免安装 MFC7xLOC.DLL 的问题。 为此，请遵循前面给出的静态情况的同一指示（将 RC 命令行正确设置为指向本地化资源)，只不过您还必须删除 AppWizard 添加的 `/D_AFXDLL` 定义。 定义 `/D_AFXDLL` 后，AFXRES.H（和其他 MFC RC 文件）实际上不会定义任何资源（因为它们将从 MFC DLL 拉取）。  
  
## <a name="see-also"></a>另请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

