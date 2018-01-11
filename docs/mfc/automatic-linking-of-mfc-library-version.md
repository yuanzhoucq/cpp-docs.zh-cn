---
title: "自动链接 MFC 库版本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: defaultlib
dev_langs: C++
helpviewer_keywords:
- defaultlib in MFC
- automatic links [MFC]
- MFC libraries, linking to
- linking [MFC], automatic of MFC library version
- linking [MFC]
- linking [MFC], of MFC
- MFC libraries, versions
ms.assetid: 02af4a20-2034-4fce-b200-c2202c3c8311
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ddc156d8518318a686796a25e89ee84a9a67ee59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="automatic-linking-of-mfc-library-version"></a>自动链接 MFC 库版本
在 3.0 版之前的 MFC 版本中（Visual C++ 2.0 版之前），您必须在链接器的库的输入列表中手动指定正确版本的 MFC 库。 在 MFC 3.0 版及更高版本中，不再需要手动指定 MFC 库的版本。 相反，MFC 标头文件自动确定正确版本的 MFC 库中，使用定义的值为基础的`#define`，如**_DEBUG**或**_UNICODE**。 MFC 标头文件添加**/defaultlib**指令来指示链接器链接 MFC 库的特定版本。  
  
 例如，以下来自 AFX.H 标头文件的代码片段指示链接器链接到 NAFXCW.LIB 或 NAFXCWD.LIB 版的 MFC 中，具体取决于是否使用了调试版的 MFC：  
  
```c++
#ifndef _UNICODE 
#ifdef _DEBUG
#pragma comment(lib, "nafxcwd.lib")
#else
#pragma comment(lib, "nafxcw.lib")
#endif
#else
#ifdef _DEBUG
#pragma comment(lib, "uafxcwd.lib")
#else
#pragma comment(lib, "uafxcw.lib")
#endif
#endif
```  
  
 MFC 标头文件还将链接到所有需要的库中，包括 MFC 库、Win32 库、OLE 库、从示例生成的 OLE 库、ODBC 库等。 Win32 库包含 Kernel32.Lib、User32.Lib 和 GDI32.Lib。  
  
## <a name="see-also"></a>请参阅  
 [MFC 库版本](../mfc/mfc-library-versions.md)

