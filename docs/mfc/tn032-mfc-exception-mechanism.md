---
title: TN032:异常机制
ms.date: 11/04/2016
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 5b419fdcc4f20579b1a809dd8a5cf6a93f4fe835
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611414"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032:异常机制

以前版本的视觉对象C++不支持标准C++异常机制和 MFC 中提供的宏**TRY/CATCH/THROW**改为使用的。 此版本的 Visual C++ 完全支持 C++ 异常。 本说明包含以前的宏的高级实现详细信息，包括如何自动清理基于堆栈的对象。 由于 C++ 异常默认支持堆栈展开，此技术说明不再是必需的。

请参阅[异常：使用 MFC 宏和C++异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)有关 MFC 宏和新的差异的详细信息C++关键字。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
