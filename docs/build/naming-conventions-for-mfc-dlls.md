---
title: "MFC Dll 命名约定 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC libraries [C++], naming conventions
- naming conventions [C++], MFC DLLs
- MFC DLLs [C++], naming conventions
- libraries [C++], MFC DLL names
- shared DLL versions [C++]
- DLLs [C++], naming conventions
- DLLs [C++], library names
ms.assetid: 0db9c3f3-87d3-40e8-8964-250f9d2a2209
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4f7702e9babcc4769136d6deab63b627f8b09bd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="naming-conventions-for-mfc-dlls"></a>MFC DLL 命名约定
Dll 和包含在 MFC 库按照结构化的命名约定。 这使得更轻松地确定哪些 DLL 或库你应使用为哪些目的。  
  
 需生成应用程序或使用这些 Dll 的 MFC 扩展 Dll 导入库拥有与 DLL 相同的基名称，但有.lib 文件扩展名。  
  
### <a name="shared-dll-naming-convention"></a>共享的 DLL 命名约定  
  
|DLL|描述|  
|---------|-----------------|  
|MFCx0.DLL|MFC DLL，ANSI 发行版本|  
|MFCx0U.DLL|MFC DLL，Unicode 发行版本|  
|MFCx0D.DLL|MFC DLL，ANSI 调试版本|  
|MFCx0UD.DLL|MFC DLL，Unicode 调试版本|  
  
 如果你要动态链接到共享的 DLL 版本的 MFC，，它从应用程序还是从 MFC 扩展 DLL，则必须与你的产品包括 MFCx0.DLL。 如果你的应用程序中需要 Unicode 支持，请改为包括 MFCx0U.DLL。  
  
 如果您以静态方式链接到 MFC DLL，你必须将其与其中一个静态 MFC 库链接。 根据约定命名这些版本 [N &#124;U] AFXCW [D]。LIB。 有关详细信息，请参阅 》 中表"静态链接库命名约定"[库命名约定](../mfc/library-naming-conventions.md)(MFC)。  
  
 可以与应用程序分发的 Visual c + + Dll 的列表，请参阅在 Visual Studio 安装中的 Redist.txt。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [库命名约定](../mfc/library-naming-conventions.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)