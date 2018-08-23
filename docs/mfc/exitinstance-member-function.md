---
title: ExitInstance 成员函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords: []
dev_langs:
- C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 954d2248061ec571d9d2ba8804c1f7c97275cbfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343494"
---
# <a name="exitinstance-member-function"></a>ExitInstance 成员函数
[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance)类的成员函数[CWinApp](../mfc/reference/cwinapp-class.md)一份你的应用程序终止时，通常因为用户退出应用程序每次调用。  
  
 如果需要特殊清理处理（如释放图形设备接口 (GDI) 资源或释放在程序执行期间使用的内存），则重写 `ExitInstance`。 但是，标准项（如文档和视图）的清理由框架使用用于执行特定于这些对象的特殊清理的其他可重写函数提供。  
  
## <a name="see-also"></a>请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
