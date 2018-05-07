---
title: ActiveX 控件容器： 将控件插入控件容器应用程序 |Microsoft 文档
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
ms.openlocfilehash: 716c045fc10b4dd5f3dede20a233d958e669bbd7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX 控件容器：将控件插入控件容器应用程序
你可以从 ActiveX 控件容器应用程序访问 ActiveX 控件之前，必须将 ActiveX 控件添加到容器应用程序使用[插入 ActiveX 控件](../windows/insert-activex-control-dialog-box.md)对话框。  
  
 若要将 ActiveX 控件添加到 ActiveX 控件容器项目，请参阅[查看和添加到对话框中的 ActiveX 控件](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。  
  
 将添加该控件后，你需要将 （的 ActiveX 控件类型） 的成员变量添加到对话框类。 有关此过程的详细信息，请参阅[添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)。  
  
 一旦你已添加成员变量类，称为包装器类，自动生成并添加到你的项目。 此类用作控件容器和嵌入的控件之间的接口。  
  
## <a name="see-also"></a>请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)

