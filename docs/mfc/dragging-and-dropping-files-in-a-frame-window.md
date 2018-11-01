---
title: 拖放框架窗口中的文件
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
ms.openlocfilehash: 34fb6ec6d57bcf8bc1cf51a3ac0c0db5203b3ffa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498813"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>拖放框架窗口中的文件

框架窗口管理与文件资源管理器或文件管理器的关系。

通过添加一些初始化调用中的重写`CWinApp`成员函数`InitInstance`，如中所述[CWinApp： 应用程序类](../mfc/cwinapp-the-application-class.md)，你可以在框架窗口间接打开的文件从文件拖放资源管理器或文件管理器和拖放框架窗口中。 请参阅[文件管理器拖放](../mfc/special-cwinapp-services.md)。

## <a name="see-also"></a>请参阅

[使用框架窗口](../mfc/using-frame-windows.md)

