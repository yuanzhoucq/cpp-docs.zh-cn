---
title: 可重写 CWinApp 成员函数
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 9f1098e305606df9463e308466b7864b019d5a00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459272"
---
# <a name="overridable-cwinapp-member-functions"></a>可重写 CWinApp 成员函数

[CWinApp](../mfc/reference/cwinapp-class.md)提供了几项可重写成员函数 (`CWinApp`重写这些成员从类[CWinThread](../mfc/reference/cwinthread-class.md)、 从中`CWinApp`派生):

- [InitInstance](../mfc/initinstance-member-function.md)

- [运行](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

唯一一个必须重写的 `CWinApp` 成员函数是 `InitInstance`。

## <a name="see-also"></a>请参阅

[CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
