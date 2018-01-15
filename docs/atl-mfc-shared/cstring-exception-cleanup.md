---
title: "CString 异常清理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 496fdfe6a609bd4eceae225c2568c915d38aef07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cstring-exception-cleanup"></a>CString 异常清理
在以前版本的 MFC，这是重要在清理[CString](../atl-mfc-shared/reference/cstringt-class.md)后使用的对象。 使用 MFC 3.0 版及更高版本，显式清理不再是必需的。  
  
 在 c + + 异常处理 MFC 现在使用的机制，无需担心在出现异常后清理。 有关说明 c + +"展开"堆栈后捕获了一个异常，请参阅[try、 catch 和 throw 语句](../cpp/try-throw-and-catch-statements-cpp.md)。 即使您使用 MFC**重**/**捕获**宏而不是 c + + 关键字**重**和**捕获**，MFC 使用 c + +异常机制下方，因此你仍不需要显式清理。  
  
## <a name="see-also"></a>请参阅  
 [字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [异常处理](../mfc/exception-handling-in-mfc.md)

