---
title: "TN057：MFC 组件的本地化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.components"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "组件 [MFC], 本地化"
  - "DLL [C++], 本地化 MFC"
  - "本地化 [C++], MFC 组件"
  - "本地化 [C++], MFC 资源"
  - "本地化 [C++], 资源"
  - "MFC DLL [C++], 本地化"
  - "资源 [MFC], 本地化"
  - "TN057"
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN057：MFC 组件的本地化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释说明某些可以使用本地化组件的设计和过程，因此，如果应用程序或如何使用 MFC 的 OLE 控件或 DLL。  
  
## 概述  
 真正理解两个解决的问题，当本地化使用 MFC 的组件。  首先，必须本地化的资源字符串、对话框和特定于组件的其他资源。  大多数组件生成也使用 MFC 中并且使用被 MFC 定义的资源。  必须提供本地化的 MFC 资源。  所幸，MFC 还提供多种语言。  
  
 此外，在其目标环境 \(或 DBCS 欧洲启用的环境\) 应准备组件运行。  在很大程度上，这取决于被视为字符的高位正确设置和处理具有双字节字符字符串的应用程序。  MFC 为这两个环境启用，默认情况下，此类使用与的，具有对不同资源的所有平台在将时间的唯一是全球性二进制是可能的。  
  
## 本地化组件中的资源  
 本地化应用程序或 DLL 应涉及替换资源与匹配区域性的资源。  对于的资源，这是相对简单：在资源编辑器编辑的资源并生成应用程序。  如果代码未正确编写将字符串文本或要本地化硬编码到 C\+\+ 源代码 \- 所有本地化可供修改资源完成。  事实上，您可以实现组件的所有本地化版本提供根本不涉及原始代码的版本。  这更复杂，但很值并用于选择 MFC 的机制。  通过直接加载 EXE 或 DLL 文件导入和资源编辑器编辑资源本地化应用程序也是可能的。  在可能时，它要求那些更改的 reapplication，每次生成应用程序的新版本。  
  
 查找是在一个单独的 DLL 的所有资源的一种避免，有时称为附属 DLL。  此 DLL 动态然后在运行时加载资源，则该 DLL 加载而不是从主模块使用任何代码。  MFC 直接支持此方法。  考虑一应用程序调用 MYAPP.EXE;它可能在 DLL 中的所有调用 MYRES.DLL 其资源。  在应用程序 `InitInstance` 将执行下加载该 DLL 和使 MFC 该位置加载资源：  
  
```  
CMyApp::InitInstance()  
{  
   // one of the first things in the init code  
   HINSTANCE hInst = LoadLibrary("myres.dll");  
   if (hInst != NULL)  
      AfxSetResourceHandle(hInst);  
  
   // other initialization code would follow  
   .  
   .  
   .  
}  
```  
  
 从该字符，MFC 将该 DLL 加载资源而非从 myapp.exe。  所有资源，但是，必须存在该 DLL;MFC 不搜索应用程序实例寻找特定资源。  此技术同样正常适用于常规 DLL 以及 OLE 控件。  安装程序将资源复制设置用户区域需要选择 MYRES.DLL 的正确版本。  
  
 仅创建资源 DLL 是相对简单。  您创建 DLL 项目，.rc 文件添加到，并将所需的资源。  如果有未使用此技术的一个现有项目，可以复制该项目的资源。  在将资源文件之后添加到项目，则几乎准备生成项目。  必须进行的唯一操作设置为包括 **\/NOENTRY**的链接器选项。  此通知链接器 DLL 没有入口点\)，因为它没有代码，但没有 EntryPoint。  
  
> [!NOTE]
>  在 Visual C\+\+ 4.0 和更高的资源编辑器支持多种语言为 .rc 文件。  这使得很容易管理在单个项目的本地化。  每种语言的资源由资源编辑器生成的预处理器指令的控制。  
  
## 使用 MFC 提供的本地化资源  
 您生成重新使用从 MFC 的两点的所有 MFC 应用程序：代码和资源。  也就是说 MFC 有多种错误消息、内置对话框的 MFC 类使用的其他资源。  完全本地化应用程序，不仅需要本地化应用程序的资源，而且还，来自直接 MFC 的资源。  MFC 自动提供许多不同语言的资源文件，因此，如果面向的语言已是一语言 MFC 支持，需要确定所使用某些本地化资源。  
  
 中文到此文本、MFC 支持，用于德语、西班牙语、法语、意大利语、日语和朝鲜语\)。  包含这些本地化版本的文件采用本地化的 MFC\) 目录的\\INCLUDE\\L.\* \(the 'L "位置）。  例如，德语 MFC 在文件\\INCLUDE\\L.DEU。  若要生成应用程序使用这些 RC 文件代替中的文件在 MFC \\INCLUDE，请将 `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` 添加到 RC 命令行 \(这是一个示例；您需要重写您安装 Visual C\+\+\) 选择以及目录的区域设置。  
  
 以上指令仍有效，如果应用程序静态链接使用 MFC。  大多数应用程序动态链接 \(因为这是 AppWizard 默认\)。  在这种情况下，不仅代码动态链接 \-，因此是资源。  因此，您可以在应用程序中的本地化资源，MFC 实现，但资源将被加载来自 MF C7 x.DLL \(或更高版本\) 或从 xLOC.DLL MF C7，如果该文件存在。  可以处理这两个不同的角度。  
  
 复杂的方法是提供了本地化的 MF C7 xLOC.DLLs \(如 MF C7 xDEU，德语、西班牙语 MF C7 的 xESP.DLL 的等\)，或更高版本，再安装相应的 xLOC.DLL MF C7 到系统目录，在用户安装应用程序时。  这非常复杂的开发人员，而作为不建议这样最终用户。  参见 [技术说明 56](../mfc/tn056-installation-of-localized-mfc-components.md) 有关此技术及其警告的更多信息。  
  
 最简单且最安全的方法是对包含在应用程序的本地化资源或 MFC DLL \(或附属 DLL，则它使用了\)。  这避免相应安装问题 xLOC.DLL MF C7。  为此，请遵循为的静态情况相同的指令前面 \(适当设置 RC 命令行到本地化资源的点\)，除此之外，由添加的 AppWizard 还必须移除 `/D_AFXDLL` 定义。  在 `/D_AFXDLL` 后，AFXRES.H \(和其他 MFC " RC 文件\) 实际上不定义任何资源 \(因为它们从 MFC DLL 将请求\)。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)