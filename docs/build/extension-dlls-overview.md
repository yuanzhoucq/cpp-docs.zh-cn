---
title: 扩展 Dll:概述
ms.date: 05/06/2019
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: ea8e950e28907ea1a4a85c1f39392d5505f08c49
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221372"
---
# <a name="mfc-extension-dlls-overview"></a>MFC 扩展 Dll:概述

MFC 扩展 DLL 是通常实现从现有的 Microsoft 基础类库类派生的可重用类的 DLL。 MFC 扩展 Dll 是使用 MFC （也称为共享的 MFC 版本） 的动态链接库版本构建的。 MFC 的可执行文件 （应用程序或规则 MFC Dll） 使用共享 MFC 版本构建的可以使用 MFC 扩展 DLL。 MFC 扩展 DLL，可从 MFC 派生新的自定义类，并再提供此扩展的版本的 MFC 应用程序调用 DLL 的。

扩展 Dll 还可以用于应用程序和 DLL 之间传递 MFC 派生的对象。 创建对象时的模块中存在与所传递的对象相关联的成员函数。 由于使用共享的 MFC DLL 版本时正确导出了这些函数，因此可以自由地传递 MFC 或应用程序和 MFC 扩展 Dll 加载之间 MFC 派生的对象指针。

有关以满足基本需求的 MFC 扩展 DLL 的 DLL 的示例，请参阅 MFC 示例[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)。 具体而言，看 Testdll1.cpp 和 Testdll2.cpp 文件。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [初始化 MFC 扩展 DLL](run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [MFC 扩展 DLL](extension-dlls.md)

- [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [非 MFC DLL：概述](non-mfc-dlls-overview.md)

- [静态链接到 MFC 的规则 MFC Dll](regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC Dll](regular-dlls-dynamically-linked-to-mfc.md)

- [创建 MFC DLL](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>请参阅

[DLL 的类型](kinds-of-dlls.md)
