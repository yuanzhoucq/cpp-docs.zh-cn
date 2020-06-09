---
title: 可重写 CWinApp 成员函数
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 7ae72a52c37582f8398ebc03f404ff105fe14650
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624014"
---
# <a name="overridable-cwinapp-member-functions"></a>可重写 CWinApp 成员函数

[CWinApp](reference/cwinapp-class.md)提供几个关键可重写成员函数（ `CWinApp` 从派生的类[CWinThread](reference/cwinthread-class.md)重写这些成员 `CWinApp` ）：

- [InitInstance](initinstance-member-function.md)

- [Run](run-member-function.md)

- [ExitInstance](exitinstance-member-function.md)

- [OnIdle](onidle-member-function.md)

唯一一个必须重写的 `CWinApp` 成员函数是 `InitInstance`。

## <a name="see-also"></a>另请参阅

[CWinApp：应用程序类](cwinapp-the-application-class.md)
