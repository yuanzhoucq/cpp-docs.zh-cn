---
title: "MFC 应用程序中的本地化资源： 附属 Dll |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc97e73998c581a40ed7d344b1ade5ca90b94ac2
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>MFC 应用程序中的本地化资源：附属 DLL
MFC 7.0 和更高版本提供对附属 Dll，该功能有助于创建针对多个语言进行本地化的应用程序的增强的支持。 附属 DLL 是[纯资源 DLL](../build/creating-a-resource-only-dll.md) ，其中包含针对特定语言进行本地化的应用程序的资源。 当应用程序开始执行时，MFC 将自动加载已本地化的资源最适合于环境。 例如，你可以使用两个附属 Dll，一个包含你的资源和另一个包含德语翻译的法语翻译的英语资源的应用程序。 当在英语语言的系统上运行应用程序时，它会使用英语资源。 如果在法语系统上运行，它将使用的法语资源;如果德语的系统上运行，则使用德语的资源。  
  
 为了支持本地化的资源在 MFC 应用程序，MFC 尝试加载附属 DLL 包含资源本地化为特定语言。 附属 Dll 名为*ApplicationNameXXX*.dll，其中*ApplicationName*是.exe 或.dll 使用 MFC 的名称和*XXX*是语言的三个字母代码资源 （例如，ENU 或 DEU）。  
  
 MFC 将尝试为每个顺序情况下，在找到时停止以下语言加载资源 DLL:  
  
1. 当前用户的默认用户界面语言，如从 GetUserDefaultUILanguage() Win32 API 返回。  
  
2.  当前用户的默认用户界面语言，没有任何特定次语言 （即，ENC [加拿大英语] 将成为 ENU [美国英语]）。  
  
3.  系统的默认用户界面语言，如从 GetSystemDefaultUILanguage() API 返回。 在其他平台上，这是本身的操作系统的语言。  
  
4.  系统的默认用户界面语言，没有任何特定次语言。  
  
5.  使用 3 个字母代码 loc。 的假语言  
  
 如果 MFC 未找到任何附属 Dll，它使用任何资源包含在应用程序本身。  
  
 例如，假设应用程序 LangExample.exe 使用 MFC 和多个用户界面系统; 上运行系统 UI 语言是 ENU [美国英语] 和当前用户的 UI 语言设置为 FRC [加拿大法语]。 MFC 查找以下 Dll 按以下顺序：  
  
1.  LangExampleFRC.dll （用户的 UI 语言）。  
  
2.  LangExampleFRA.dll （没有次语言，在此示例中法语 （法国） 的用户的用户界面语言。  
  
3.  LangExampleENU.dll （系统的 UI 语言）。  
  
4.  LangExampleLOC.dll。  
  
 如果没有这些 Dll 会发现，MFC 在 LangExample.exe 中使用的资源。  
  
## <a name="see-also"></a>请参阅  
 [Visual c + + 中的 Dll](../build/dlls-in-visual-cpp.md)   
 [TN057：MFC 组件的本地化](../mfc/tn057-localization-of-mfc-components.md)