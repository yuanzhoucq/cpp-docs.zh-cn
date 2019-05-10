---
title: Active 技术和 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
ms.openlocfilehash: f67fb9548601ac705ceda08d20d3049f0bf1e0a5
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220996"
---
# <a name="active-technology-and-dlls"></a>Active 技术和 DLL

Active 技术使对象服务器得以在 DLL 内完全实现。 此类服务器称为进程内服务器。 MFC 不完全支持进程内服务器的可视化编辑的所有功能主要是因为 Active 技术不提供服务器挂接到容器的主消息循环的一种方法。 MFC 需要访问容器应用程序的消息循环来处理加速键和空闲处理。

如果你正在编写自动化服务器和你的服务器具有的用户界面，可以使您的服务器成为进程内服务器并将其完全置于 DLL。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [自动化服务器](../mfc/automation-servers.md)

## <a name="see-also"></a>请参阅

[创建 C /C++ Visual Studio 中的 Dll](dlls-in-visual-cpp.md)
