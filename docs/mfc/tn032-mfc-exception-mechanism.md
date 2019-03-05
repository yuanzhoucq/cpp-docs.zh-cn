---
title: TN032:异常机制
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.exceptions
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 210e47e117cd602ba77edd330205385f54199ce5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288748"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032:异常机制

以前版本的 Visual c + + 不支持标准 c + + 异常机制，和 MFC 中提供的宏**TRY/CATCH/THROW**改为使用的。 此版本的 Visual C++ 完全支持 C++ 异常。 本说明包含以前的宏的高级实现详细信息，包括如何自动清理基于堆栈的对象。 由于 C++ 异常默认支持堆栈展开，此技术说明不再是必需的。

请参阅[异常：使用 MFC 宏和 c + + 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)有关 MFC 宏和新的 c + + 关键字之间的差异的详细信息。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
