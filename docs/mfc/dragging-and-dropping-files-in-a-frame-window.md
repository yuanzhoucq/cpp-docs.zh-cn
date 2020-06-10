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
ms.openlocfilehash: 42f21e2441f8ba3d2c6a13503c928880fe100f04
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623161"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>拖放框架窗口中的文件

框架窗口管理与文件资源管理器或文件管理器的关系。

通过在成员函数的重写中添加几个初始化调用 `CWinApp` `InitInstance` （如[CWinApp：应用程序类](cwinapp-the-application-class.md)中所述），可以使框架窗口间接打开从文件资源管理器或文件管理器中拖放到框架窗口中的文件。 请参阅[文件管理器拖放](special-cwinapp-services.md)。

## <a name="see-also"></a>另请参阅

[使用框架窗口](using-frame-windows.md)
