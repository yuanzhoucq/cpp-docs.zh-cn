---
title: "测试修改后的 ATL DHTML 控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5ecb8526ec82e0f2d18c5306a94dd7f0160803b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="testing-the-modified-atl-dhtml-control"></a>测试修改后的 ATL DHTML 控件
试用新控件，以了解它如何现在工作。  
  
#### <a name="to-build-and-test-the-modified-control"></a>若要生成并测试修改后的控件  
  
1.  重新生成项目并在测试容器中打开它。 请参阅[使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)有关如何访问测试容器的信息。  
  
     调整控件以显示所有你添加的按钮的大小。  
  
2.  检查通过更改 HTML 插入的两个按钮。 每个按钮具有您在中标识的标签[修改 ATL DHTML 控件](../atl/modifying-the-atl-dhtml-control.md):**刷新**和**HelloHTML**。  
  
3.  测试两个新的按钮，以查看它们如何工作。  
  
 现在，测试不是 UI 的一部分的方法。  
  
1.  突出显示该控件，以便激活边框。  
  
2.  上**控件**菜单上，单击**调用方法**。  
  
 标记为列表中的方法**方法名称**是容器可以调用的方法：`MethodInvoked`和`GoToURL`。 通过 UI，所有其他方法进行控制。  
  
1.  选择一个方法调用，并单击`Invoke`显示方法的消息框，或导航到 www.microsoft.com。  
  
2.  在**调用方法**对话框中，单击**关闭**。  
  
 若要了解有关各个元素和构成的 ATL DHTML 控件文件的详细信息，请参阅[确定 DHTML 控件项目元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md)。  
  
## <a name="see-also"></a>请参阅  
 [支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)

