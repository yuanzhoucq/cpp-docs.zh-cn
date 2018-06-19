---
title: DLL 中的自动化 |Microsoft 文档
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
ms.openlocfilehash: 41c5f31a72cf734296ecb281e0785d415c8043a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360649"
---
# <a name="automation-in-a-dll"></a>DLL 中的自动化
当你在 MFC DLL 向导中选择自动化选项时，该向导将提供你替换为以下内容：  
  
-   起始对象描述语言 (。ODL) 文件  
  
-   在 STDAFX.h 文件中为 Afxole.h include 指令  
  
-   实现`DllGetClassObject`函数，该调用函数**AfxDllGetClassObject**函数  
  
-   实现`DllCanUnloadNow`函数，该调用函数**AfxDllCanUnloadNow**函数  
  
-   实现`DllRegisterServer`函数，该调用函数[COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall)函数  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [自动化服务器](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)