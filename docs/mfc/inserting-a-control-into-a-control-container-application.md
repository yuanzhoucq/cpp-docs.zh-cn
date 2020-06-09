---
title: ActiveX 控件容器：将控件插入控件容器应用程序
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
ms.openlocfilehash: 1d2fc82628b3bcf842a6efb1d36ab9e8389fc0ba
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618497"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX 控件容器：将控件插入控件容器应用程序

在从 ActiveX 控件容器应用程序访问 ActiveX 控件之前，必须使用 "[插入 Activex 控件](../windows/insert-activex-control-dialog-box.md)" 对话框将 activex 控件添加到容器应用程序。

若要向 ActiveX 控件容器项目添加 ActiveX 控件，请参阅[查看 Activex 控件并将其添加到对话框](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。

添加控件后，需要将一个成员变量（属于 ActiveX 控件类型）添加到对话框类。 有关此过程的详细信息，请参阅[添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)。

添加成员变量后，将自动生成一个称为包装类的类，并将其添加到你的项目中。 此类用作控件容器和嵌入控件之间的接口。

## <a name="see-also"></a>另请参阅

[ActiveX 控件容器](activex-control-containers.md)
