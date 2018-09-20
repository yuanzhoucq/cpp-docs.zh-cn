---
title: 不通过代码向导对控件类型安全的访问 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2685c946b9ee1c738ee83f9413b7fd955857febb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438335"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>不通过代码向导对控件进行类型安全的访问

创建对控件的类型安全访问的第一种方法是使用内联成员函数将 `CWnd` 类的 `GetDlgItem` 成员函数的返回类型转换为适当的 C++ 控件类型，如此示例中所示：

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

然后利用类似下面这样的代码，使用此成员函数以类型安全的方式控件：

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>请参阅

[对对话框中的控件进行类型安全的访问](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[对控件进行类型安全的访问（使用代码向导）](../mfc/type-safe-access-to-controls-with-code-wizards.md)

