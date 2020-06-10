---
title: ActiveX 控件容器：查看和修改控件属性
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
ms.openlocfilehash: b0ca43f59cf70dea1348f22a08cfb4e89b45c3dd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617356"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>ActiveX 控件容器：查看和修改控件属性

将 ActiveX 控件插入项目时，查看和更改 ActiveX 控件支持的属性很有用。 本文讨论如何使用 Visual C++ 资源编辑器执行此操作。

如果 ActiveX 控件容器应用程序使用嵌入控件，则可在资源编辑器中查看和修改控件的属性。 还可在设计时使用资源编辑器设置属性值。 资源编辑器之后会将这些值自动保存在项目资源文件中。 控件的任何实例之后会将其属性初始化为这些值。

此过程假定，您已将控件插入项目中。 有关信息，请参阅[ActiveX 控件容器：将控件插入控件容器应用程序](inserting-a-control-into-a-control-container-application.md)。

查看控件属性的第一步是将控件实例添加到项目的对话框模板中。

### <a name="to-view-the-properties-of-a-control"></a>查看控件的属性

1. 在资源视图中，打开**对话框**文件夹。

1. 打开主对话框模板。

1. 使用 "**插入 Activex 控件**" 对话框插入 activex 控件。 有关详细信息，请参阅[查看 ActiveX 控件并将其添加到对话框](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。

1. 选择对话框中的 ActiveX 控件。

1. 在 "**属性**" 窗口中，单击 "**属性**" 按钮。

使用 "**属性**" 对话框可以立即修改和测试新属性。

## <a name="see-also"></a>另请参阅

[ActiveX 控件容器](activex-control-containers.md)
