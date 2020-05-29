---
title: 可重写 CWinApp 成员函数
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 28ba243bd755e25db5f2cb03d08013f082fbc918
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447261"
---
# <a name="overridable-cwinapp-member-functions"></a>可重写 CWinApp 成员函数

[CWinApp](../mfc/reference/cwinapp-class.md)提供几个关键可重写成员函数（`CWinApp` 将从派生 `CWinApp` 的类[CWinThread](../mfc/reference/cwinthread-class.md)中重写这些成员）：

- [InitInstance](../mfc/initinstance-member-function.md)

- [运行](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

唯一一个必须重写的 `CWinApp` 成员函数是 `InitInstance`。

## <a name="see-also"></a>另请参阅

[CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
