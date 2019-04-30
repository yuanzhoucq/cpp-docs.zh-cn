---
title: ExitInstance 成员函数
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: c76f588b22ad8ffd1d3dae954c5113feffb62a3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405815"
---
# <a name="exitinstance-member-function"></a>ExitInstance 成员函数

[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance)类的成员函数[CWinApp](../mfc/reference/cwinapp-class.md)一份应用程序终止时，通常因为用户退出应用程序每次调用。

如果需要特殊清理处理（如释放图形设备接口 (GDI) 资源或释放在程序执行期间使用的内存），则重写 `ExitInstance`。 但是，标准项（如文档和视图）的清理由框架使用用于执行特定于这些对象的特殊清理的其他可重写函数提供。

## <a name="see-also"></a>请参阅

[CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
