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
ms.openlocfilehash: 04cf0b06773937bf66defccbb0e5e880c06e8d88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306676"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Rich Edit 控件中的流操作

您可以使用流将数据传入或传出格式文本编辑控件 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 定义一个流[EDITSTREAM](/windows/desktop/api/richedit/ns-richedit-_editstream)结构，指定缓冲区和应用程序定义的回调函数。

若要读取数据到 rich edit 控件 （即，流式传输中的数据） 使用[StreamIn](../mfc/reference/cricheditctrl-class.md#streamin)成员函数。 此控件将重复调用应用程序定义的回调函数，以每次将部分数据传入缓冲区。

若要保存的内容丰富的编辑控件 （即，将数据流出），可以使用[StreamOut](../mfc/reference/cricheditctrl-class.md#streamout)成员函数。 此控件将反复写入缓冲区，然后调用应用程序定义的回调函数。 对于每个调用，回调函数将保存缓冲区的内容。

## <a name="see-also"></a>请参阅

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
