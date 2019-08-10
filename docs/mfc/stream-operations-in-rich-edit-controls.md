---
title: Rich Edit 控件中的流操作
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
ms.openlocfilehash: 04bf49371b3ab5eaaad2775b532d8d35bf990ce3
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915293"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Rich Edit 控件中的流操作

可以使用流将数据传入或传出丰富的编辑控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 流由[EDITSTREAM](/windows/desktop/api/richedit/ns-richedit-editstream)结构定义, 该结构指定一个缓冲区和一个应用程序定义的回调函数。

若要将数据读入富编辑控件 (即在中流式传输数据), 请使用[StreamIn](../mfc/reference/cricheditctrl-class.md#streamin)成员函数。 此控件将重复调用应用程序定义的回调函数，以每次将部分数据传入缓冲区。

若要保存 rich edit 控件的内容 (也就是说, 流式传输数据), 可以使用[StreamOut](../mfc/reference/cricheditctrl-class.md#streamout)成员函数。 此控件将反复写入缓冲区，然后调用应用程序定义的回调函数。 对于每个调用，回调函数将保存缓冲区的内容。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
