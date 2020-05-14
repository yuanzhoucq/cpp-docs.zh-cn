---
title: MFC 应用程序中已本地化的资源：附属 DLL
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
ms.openlocfilehash: 1f512cc17832564b5eb530b97f8bfb2642c43d43
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220740"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>MFC 应用程序中已本地化的资源：附属 DLL

MFC 版本 7.0 及更高版本提供对附属 DLL 的增强支持，该功能有助于创建针对多种语言进行本地化的应用程序。 附属 DLL 是[纯资源 DLL](creating-a-resource-only-dll.md)，其中包含针对特定语言本地化的应用程序资源。 当应用程序开始执行时，MFC 会自动加载最适合于环境的本地化资源。 例如，你可能会有一个具有英语语言资源的应用程序，其中包含两个附属 DLL，一个包含资源的法语翻译，另一个包含德语翻译。 当应用程序在英语语言系统上运行时，它会使用英语资源。 如果在法语系统上运行，则它会使用法语资源；如果在德语系统上运行，则它会使用德语资源。

为了支持 MFC 应用程序中的本地化资源，MFC 会尝试加载包含本地化为特定语言的资源的附属 DLL。 附属 DLL 名为 ApplicationNameXXX  .dll，其中 ApplicationName  是使用 MFC 的 .exe 或 .dll 的名称，XXX  是资源语言的三字母代码（例如，“ENU”或“DEU”）。

MFC 尝试按顺序加载以下每种语言的资源 DLL，并在找到一种时停止：

1. 当前用户的默认 UI 语言，从 GetUserDefaultUILanguage() Win32 API 返回。

1. 没有任何特定子语言的当前用户默认 UI 语言（即，ENC [加拿大英语] 会成为 ENU [美国英语]）。

1. 系统的默认 UI 语言，从 GetSystemDefaultUILanguage() API 返回。 在其他平台上，这是操作系统本身的语言。

1. 没有任何特定子语言的系统默认 UI 语言。

1. 具有 3 字母代码 LOC 的虚设语言。

如果 MFC 找不到任何附属 DLL，它将使用应用程序本身中包含的任何资源。

例如，假设应用程序 LangExample.exe 使用 MFC 并且在多用户界面系统上运行；系统 UI 语言为 ENU [美国英语]，而当前用户的 UI 语言设置为 FRC [加拿大法语]。 MFC 会按以下顺序查找以下 DLL：

1. LangExampleFRC.dll（用户的 UI 语言）。

1. LangExampleFRA.dll（没有子语言的用户 UI 语言，在此示例中为法语（法国））。

1. LangExampleENU.dll（系统的 UI 语言）。

1. LangExampleLOC.dll。

如果未找到这些 DLL，则 MFC 将使用 LangExample.exe 中的资源。

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)<br/>
[TN057：MFC 组件本地化](../mfc/tn057-localization-of-mfc-components.md)
