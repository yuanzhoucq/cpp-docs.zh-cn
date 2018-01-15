---
title: "ActiveX 控件容器： 将控件插入控件容器应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX control containers [MFC], inserting controls
- ActiveX controls [MFC], adding to projects
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a1eaaf0426726f252fc4990f06faa73b0598cfbb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-inserting-a-control-into-a-control-container-application"></a>ActiveX 控件容器：将控件插入控件容器应用程序
你可以从 ActiveX 控件容器应用程序访问 ActiveX 控件之前，必须将 ActiveX 控件添加到容器应用程序使用[插入 ActiveX 控件](../windows/insert-activex-control-dialog-box.md)对话框。  
  
 若要将 ActiveX 控件添加到 ActiveX 控件容器项目，请参阅[查看和添加到对话框中的 ActiveX 控件](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)。  
  
 将添加该控件后，你需要将 （的 ActiveX 控件类型） 的成员变量添加到对话框类。 有关此过程的详细信息，请参阅[添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)。  
  
 一旦你已添加成员变量类，称为包装器类，自动生成并添加到你的项目。 此类用作控件容器和嵌入的控件之间的接口。  
  
## <a name="see-also"></a>请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)

