---
title: 对 RichEdit 1.0 控件使用 MFC
ms.date: 11/04/2016
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
ms.openlocfilehash: 080ad995b9c7a041337d9b296d6ef8906e7f20ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468310"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>对 RichEdit 1.0 控件使用 MFC

若要使用 RichEdit 控件，必须首先调用[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)加载 RichEdit 2.0 控件 (RICHED20。DLL)，或调用[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)加载较旧的 RichEdit 1.0 控件 (RICHED32。DLL)。

可以使用当前[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)类与较旧的 RichEdit 1.0 控件，但`CRichEditCtrl`不仅旨在支持 RichEdit 2.0 控件。 RichEdit 1.0 和 RichEdit 2.0 是非常相似，因为大多数方法都有效;但请注意有一些差异的 1.0 和 2.0 的控件，因此，某些方法可能工作不正常或根本不起作用。

## <a name="requirements"></a>要求

MFC

## <a name="see-also"></a>请参阅

[对话框编辑器疑难解答](../windows/troubleshooting-the-dialog-editor.md)<br/>
[对话框编辑器](../windows/dialog-editor.md)