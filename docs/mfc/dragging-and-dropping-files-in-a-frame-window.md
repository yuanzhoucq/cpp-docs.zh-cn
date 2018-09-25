---
title: 拖动并将文件放置在框架窗口 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fc68923de531240a2d59336c79e54f6562b369c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380524"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>拖放框架窗口中的文件

框架窗口管理与文件资源管理器或文件管理器的关系。

通过添加一些初始化调用中的重写`CWinApp`成员函数`InitInstance`，如中所述[CWinApp： 应用程序类](../mfc/cwinapp-the-application-class.md)，你可以在框架窗口间接打开的文件从文件拖放资源管理器或文件管理器和拖放框架窗口中。 请参阅[文件管理器拖放](../mfc/special-cwinapp-services.md)。

## <a name="see-also"></a>请参阅

[使用框架窗口](../mfc/using-frame-windows.md)

