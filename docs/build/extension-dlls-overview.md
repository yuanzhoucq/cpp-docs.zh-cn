---
title: 扩展 Dll:概述
ms.date: 11/04/2016
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: 0ad5c82d72a3cd9b4801274aefd40d96afdbcdd1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425050"
---
# <a name="mfc-extension-dlls-overview"></a>MFC 扩展 Dll:概述

MFC 扩展 DLL 是通常实现从现有的 Microsoft 基础类库类派生的可重用类的 DLL。 MFC 扩展 Dll 是使用 MFC （也称为共享的 MFC 版本） 的动态链接库版本构建的。 MFC 的可执行文件 （应用程序或规则 MFC Dll） 使用共享 MFC 版本构建的可以使用 MFC 扩展 DLL。 MFC 扩展 DLL，可从 MFC 派生新的自定义类，并再提供此扩展的版本的 MFC 应用程序调用 DLL 的。

扩展 Dll 还可以用于应用程序和 DLL 之间传递 MFC 派生的对象。 创建对象时的模块中存在与所传递的对象相关联的成员函数。 由于使用共享的 MFC DLL 版本时正确导出了这些函数，因此可以自由地传递 MFC 或应用程序和 MFC 扩展 Dll 加载之间 MFC 派生的对象指针。

有关以满足基本需求的 MFC 扩展 DLL 的 DLL 的示例，请参阅 MFC 示例[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)。 具体而言，看 Testdll1.cpp 和 Testdll2.cpp 文件。

请注意，Visual c + + 文档中不再使用的术语 AFXDLL。 MFC 扩展 DLL 具有与以前的 AFXDLL 相同的特性。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [初始化 MFC 扩展 DLL](../build/run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [MFC 扩展 DLL](../build/extension-dlls.md)

- [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)

- [静态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [创建 MFC DLL](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>请参阅

[DLL 的类型](../build/kinds-of-dlls.md)
