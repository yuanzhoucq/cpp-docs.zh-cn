---
title: MFC 应用程序中的本地化资源：附属 DLL
ms.date: 11/04/2016
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
ms.openlocfilehash: e9f9b751da6339cbe8f352bdb7eee4b7af2c359b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657989"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>MFC 应用程序中的本地化资源：附属 DLL

MFC 版本 7.0 和更高版本提供对附属 Dll，该功能有助于创建应用程序本地化为多种语言的增强的支持。 附属 DLL 是[纯资源 DLL](../build/creating-a-resource-only-dll.md) ，其中包含针对特定语言进行本地化的应用程序的资源。 当应用程序开始执行时，MFC 将自动加载最适合于环境的本地化的资源。 例如，你可以使用两个附属 Dll，包含你的资源和另一个包含德语译文的法语翻译的英语语言资源的应用程序。 在英语语言的系统上运行应用程序时，它使用英语资源。 如果在法语系统上运行，它使用的法语资源;如果正使用德语系统上运行，则使用德语资源。

为了支持本地化的资源在 MFC 应用程序，MFC 尝试加载附属 DLL 包含资源本地化为特定语言。 附属 Dll 名为*ApplicationNameXXX*.dll，其中*ApplicationName*的.exe 或.dll 使用 MFC，名称和*XXX*是语言的三个字母代码（例如，简体中文或 DEU） 的资源。

MFC 将尝试为每个按顺序，停止时找到了以下语言版本加载资源 DLL:

1. 当前用户的默认 UI 语言，如从 GetUserDefaultUILanguage() Win32 API 返回。

1. 当前用户的默认 UI 语言，而无需任何特定的子语言 （即，ENC [加拿大英语] 将成为简体中文 [美国英文版]）。

1. 系统的默认 UI 语言，如从 GetSystemDefaultUILanguage() API 返回。 在其他平台，这是操作系统本身的语言。

1. 系统的默认 UI 语言，而无需任何特定的子语言。

1. 使用 3 个字母代码 LOC.的虚设语言

如果 MFC 未找到任何附属 Dll，它使用任何资源都包含在应用程序本身。

例如，假设应用程序 LangExample.exe 使用 MFC 和多个用户界面系统; 上运行系统 UI 语言是简体中文 [美国英语] 和当前用户的 UI 语言设置为 FRC [加拿大法语]。 MFC 将查找以下 Dll 按以下顺序：

1. LangExampleFRC.dll （用户的 UI 语言）。

1. LangExampleFRA.dll （而无需子语言，在此示例中法语 （法国） 用户的 UI 语言。

1. LangExampleENU.dll （系统 UI 语言）。

1. LangExampleLOC.dll。

如果没有这些 Dll 发现对象，MFC 在 LangExample.exe 中使用的资源。

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)<br/>
[TN057：MFC 组件的本地化](../mfc/tn057-localization-of-mfc-components.md)