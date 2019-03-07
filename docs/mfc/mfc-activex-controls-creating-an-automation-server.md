---
title: MFC ActiveX 控件：创建自动化服务器
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: 01f0162e124c5c49d45ce4a90f5243c88b09b5a0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303724"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>MFC ActiveX 控件：创建自动化服务器

可以为自动化服务器，从而以编程方式在另一个应用程序中嵌入该控件和控件中调用方法，从应用程序开发的 MFC ActiveX 控件。 此类控件仍可托管在 ActiveX 控件容器中。

### <a name="to-create-a-control-as-an-automation-server"></a>若要创建的控件作为自动化服务器

1. [创建](../mfc/reference/mfc-activex-control-wizard.md)控件。

1. [将方法添加](../mfc/mfc-activex-controls-methods.md)。

1. 重写[IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed)。

1. 生成控件。

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>若要以编程方式访问自动化服务器中的方法

1. 创建应用程序，例如， [MFC exe](../mfc/reference/mfc-application-wizard.md)。

1. 在开头`InitInstance`函数中，添加以下行：

   [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. 在类视图中，右键单击项目节点并选择**从类型库添加类**导入类型库。

   这将添加到项目的包含文件扩展名为.h 和.cpp 文件。

1. 在其中你将调用 ActiveX 控件中的一个或多个方法的类标头文件，添加以下行： `#include filename.h`，其中文件名是导入类型库时已创建的标头文件的名称。

1. 在函数调用将对 ActiveX 控件中的方法中，添加用于创建控件的包装器类的对象代码并创建 ActiveX 对象。 例如，下面的 MFC 代码实例化`CCirc`控件，获取 Caption 属性，并在对话框中单击确定按钮时显示结果：

   [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

如果将方法添加到 ActiveX 控件使用的应用程序中后，可以开始通过删除文件导入类型库时创建的应用程序中使用该控件的最新版本。 然后再次导入类型库。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)
