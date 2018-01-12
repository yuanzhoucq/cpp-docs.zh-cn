---
title: "动态链接库支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- regular MFC DLLs [MFC], project targets as DLLs
- DLLs [MFC], MFC
- NAFXDW.LIB
- MFC DLLs [MFC], regular MFC DLLs
- USRDLLs, DLL support
- NAFXDWD.LIB
ms.assetid: cc31c69f-3c78-4db1-9ecd-0fd8dc3217e3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 394c48644c3b5cdc2514fefef2f4451e4098856f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dynamic-link-library-support"></a>动态链接库支持
NAFXCW.lib 和 NAFXCWD.lib 库 (静态链接库命名约定表中列出[库命名约定](../mfc/library-naming-conventions.md)) 创建你的项目作为一个名为"正则 MFC DLL"的动态链接库 (以前称为"USRDLL")可与不使用类库生成的应用程序。 此 DLL 不支持 MFCx0.DLL 和 MFCx0D.DLL （称为 AFXDLL），其中包含在 DLL 中的整个类库相同。 有关详细信息，请参阅[Dll](../build/dlls-in-visual-cpp.md)。 DLL 名称的表，请参阅[MFC Dll 的命名约定](../build/naming-conventions-for-mfc-dlls.md)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 库版本](../mfc/mfc-library-versions.md)

