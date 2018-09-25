---
title: ActiveX 控件容器： 将控件插入控件容器应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f025c9fa564bcd37c585db6ea5c5cd0f5be83e0d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432134"
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX 控件容器：将控件插入控件容器应用程序

可以从 ActiveX 控件容器应用程序访问 ActiveX 控件之前，必须将 ActiveX 控件添加到容器应用程序中使用[插入 ActiveX 控件](../windows/insert-activex-control-dialog-box.md)对话框。

若要将 ActiveX 控件添加到 ActiveX 控件容器项目，请参阅[查看和添加到对话框中的 ActiveX 控件](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。

一旦添加了控件，您需要向对话框类中添加成员变量 （的 ActiveX 控件类型）。 此过程的详细信息，请参阅[添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)。

一旦您已添加成员变量一个类，称为包装器类自动生成并添加到你的项目。 此类用作控件容器和嵌入的控件之间的接口。

## <a name="see-also"></a>请参阅

[ActiveX 控件容器](../mfc/activex-control-containers.md)

