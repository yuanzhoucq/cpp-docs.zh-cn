---
title: 可重写 CWinApp 成员函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d454ce65a2068a00f9b2c7f5934951f295738c12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="overridable-cwinapp-member-functions"></a>可重写 CWinApp 成员函数
[CWinApp](../mfc/reference/cwinapp-class.md)提供了几项可重写成员函数 (`CWinApp`重写这些成员从类[CWinThread](../mfc/reference/cwinthread-class.md)，从中`CWinApp`派生):  
  
-   [InitInstance](../mfc/initinstance-member-function.md)  
  
-   [运行](../mfc/run-member-function.md)  
  
-   [ExitInstance](../mfc/exitinstance-member-function.md)  
  
-   [OnIdle](../mfc/onidle-member-function.md)  
  
 唯一一个必须重写的 `CWinApp` 成员函数是 `InitInstance`。  
  
## <a name="see-also"></a>请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
