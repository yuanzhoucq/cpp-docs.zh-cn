---
title: MFC ActiveX 控件：从方法返回错误代码
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
ms.openlocfilehash: 5314545a3a903158362dbfa65c4a9a1b2143e86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364542"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX 控件：从方法返回错误代码

本文介绍如何通过 ActiveX 控件方法返回错误代码。

要指示方法内发生错误，应使用[COleControl：throwError](../mfc/reference/colecontrol-class.md#throwerror)成员函数，该函数以 SCODE（状态代码）为参数。 您可以使用预定义的 SCODE 或定义您自己的 SCODE。

> [!NOTE]
> `ThrowError` 意味着仅用作通过属性的 Get 或 Set 函数或自动化方法返回错误的一种方式。 这是适当异常处理程序将出现在堆栈上的唯一时间。

帮助器函数存在于最常见的预定义的 SCOD 中，例如[COleControl：设置不受支持](../mfc/reference/colecontrol-class.md#setnotsupported)[、COleControl：：未受支持](../mfc/reference/colecontrol-class.md#getnotsupported)，以及[COleControl：设置不允许](../mfc/reference/colecontrol-class.md#setnotpermitted)。

有关预定义的 SCOD 列表和有关定义自定义 SCOD 的说明，请参阅[ActiveX 控件中的 ActiveX 控件中的"处理错误](../mfc/mfc-activex-controls-advanced-topics.md)"部分：高级主题。

有关在代码的其他区域中报告异常的详细信息，请参阅[COleControl：：FireError](../mfc/reference/colecontrol-class.md#fireerror)和[ActiveX 控件中"处理活动X"控件中的错误](../mfc/mfc-activex-controls-advanced-topics.md)部分：高级主题。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)
