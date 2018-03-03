---
title: "MFC ActiveX 控件： 创建自动化服务器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c3de04fbbfa9f2d0b55b7e31ca02faeddfa5c12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>MFC ActiveX 控件：创建自动化服务器
你可以为自动化服务器，从而以编程方式在另一个应用程序中嵌入该控件和控件中调用方法，从应用程序开发 MFC ActiveX 控件。 此类控件也仍可用于承载 ActiveX 控件容器中。  
  
### <a name="to-create-a-control-as-an-automation-server"></a>若要创建的控件为自动化服务器  
  
1.  [创建](../mfc/reference/mfc-activex-control-wizard.md)控件。  
  
2.  [将方法添加](../mfc/mfc-activex-controls-methods.md)。  
  
3.  重写[IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed)。 有关详细信息，请参阅知识库文章 Q146120。  
  
4.  生成控件。  
  
### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>以编程方式访问自动化服务器中的方法  
  
1.  创建应用程序，例如， [MFC exe](../mfc/reference/mfc-application-wizard.md)。  
  
2.  开头的`InitInstance`函数中，添加以下行：  
  
     [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]  
  
3.  在类视图中，右键单击项目节点并选择**从类型库添加类**导入类型库。  
  
     这将向项目添加文件扩展名为.h 和.cpp 文件。  
  
4.  在你将在其中调用 ActiveX 控件中存在一个或多个方法的类标头文件，添加以下行： `#include filename.h`，其中文件名称是导入类型库时已创建的标头文件的名称。  
  
5.  在函数调用将对 ActiveX 控件中的方法中，将创建控件的包装器类的对象的代码添加和创建 ActiveX 对象。 例如，下面的 MFC 代码实例化`CCirc`控件，获取的标题属性中，然后在对话框中单击确定按钮时显示的结果：  
  
     [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]  
  
 如果应用程序中使用后，你可以将方法添加到 ActiveX 控件，你可以开始使用应用程序中的控件的最新版本，通过删除时导入类型库创建的文件。 然后再次导入类型库。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

