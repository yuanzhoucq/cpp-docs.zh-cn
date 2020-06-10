---
title: MFC ActiveX 控件：创建自动化服务器
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: f2c941e43e810845560b4c35c558ec70248c21ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622383"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>MFC ActiveX 控件：创建自动化服务器

可以将 MFC ActiveX 控件作为自动化服务器开发，以便以编程方式将该控件嵌入另一个应用程序，并从应用程序调用控件中的方法。 此类控件仍可在 ActiveX 控件容器中托管。

### <a name="to-create-a-control-as-an-automation-server"></a>创建控件作为自动化服务器

1. [创建](reference/mfc-activex-control-wizard.md)控件。

1. [添加方法](mfc-activex-controls-methods.md)。

1. 重写[IsInvokeAllowed](reference/colecontrol-class.md#isinvokeallowed)。

1. 生成控件。

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>以编程方式访问自动化服务器中的方法

1. 创建一个应用程序，例如[MFC exe](reference/mfc-application-wizard.md)。

1. 在函数的开头 `InitInstance` ，添加以下行：

   [!code-cpp[NVC_MFC_AxCont#17](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. 在类视图中，右键单击项目节点，然后选择 "**从 Typelib 添加类**" 以导入类型库。

   这会将文件扩展名为 .h 和 .cpp 的文件添加到项目。

1. 在将在其中调用 ActiveX 控件中的一个或多个方法的类头文件中，添加以下行： `#include filename.h` ，其中 file name 是导入类型库时创建的标头文件的名称。

1. 在将对 ActiveX 控件中的方法进行调用的函数中，添加创建控件包装器类的对象的代码，并创建 ActiveX 对象。 例如，以下 MFC 代码将实例化 `CCirc` 控件，获取 Caption 属性，并在对话框中单击 "确定" 按钮时显示结果：

   [!code-cpp[NVC_MFC_AxCont#18](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

如果在应用程序中使用 ActiveX 控件后将这些方法添加到 ActiveX 控件，则可以通过删除在导入类型库时创建的文件，开始在应用程序中使用最新版本的控件。 然后再次导入类型库。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
