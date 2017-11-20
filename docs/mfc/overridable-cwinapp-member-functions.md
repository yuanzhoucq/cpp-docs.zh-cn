---
title: "可重写 CWinApp 成员函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CWinApp
dev_langs: C++
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3de4444aaeb55ab30ec6ce7e0ebd187c8468f673
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="overridable-cwinapp-member-functions"></a>可重写 CWinApp 成员函数
[CWinApp](../mfc/reference/cwinapp-class.md)提供了几项可重写成员函数 (`CWinApp`重写这些成员从类[CWinThread](../mfc/reference/cwinthread-class.md)，从中`CWinApp`派生):  
  
-   [InitInstance](../mfc/initinstance-member-function.md)  
  
-   [运行](../mfc/run-member-function.md)  
  
-   [ExitInstance](../mfc/exitinstance-member-function.md)  
  
-   [OnIdle](../mfc/onidle-member-function.md)  
  
 唯一一个必须重写的 `CWinApp` 成员函数是 `InitInstance`。  
  
## <a name="see-also"></a>另请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
