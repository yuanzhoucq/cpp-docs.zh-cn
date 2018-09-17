---
title: DLL 中的自动化 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cde5d0e400f1bdd3f5a851d47da581380273b04a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717766"
---
# <a name="automation-in-a-dll"></a>DLL 中的自动化

当在 MFC DLL 向导中选择自动化选项时，向导将为您提供以下：

- 起始对象描述语言 (。ODL) 文件

- 在 STDAFX.h 文件中为 Afxole.h include 指令

- 实现`DllGetClassObject`函数，调用**AfxDllGetClassObject**函数

- 实现`DllCanUnloadNow`函数，调用**AfxDllCanUnloadNow**函数

- 实现`DllRegisterServer`函数，调用[COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall)函数

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [自动化服务器](../mfc/automation-servers.md)

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)