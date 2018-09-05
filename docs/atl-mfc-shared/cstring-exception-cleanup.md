---
title: CString 异常清理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 656739ad000612f130f5cdfb1a53a6de2d67c4c8
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761363"
---
# <a name="cstring-exception-cleanup"></a>CString 异常清理

在以前版本的 MFC，很重要，清理[CString](../atl-mfc-shared/reference/cstringt-class.md)后使用的对象。 MFC 3.0 版及更高版本中，使用显式清理不再是必需的。

在 c + + 异常处理 MFC 现在使用的机制，无需担心在发生异常后清理。 有关如何说明 c + +"展开"堆栈捕获到异常后，请参阅[try、 catch 和 throw 语句](../cpp/try-throw-and-catch-statements-cpp.md)。 即使您使用 MFC**尝试**/**CATCH**宏而不是 c + + 关键字**尝试**并**捕获**，MFC 使用 c + +异常机制下，因此你仍不需要显式清除。

## <a name="see-also"></a>请参阅

[字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
[异常处理](../mfc/exception-handling-in-mfc.md)

