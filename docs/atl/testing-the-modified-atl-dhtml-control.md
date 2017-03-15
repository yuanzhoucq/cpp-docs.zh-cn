---
title: "Testing the Modified ATL DHTML Control | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DHTML controls, 测试"
  - "HTML 控件, 测试"
  - "testing controls"
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Testing the Modified ATL DHTML Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试您的新控件从而了解现在可以使用。  
  
#### 生成并测试修改的控件  
  
1.  重新生成项目并打开该测试容器。  有关如何访问测试容器的信息，请参见 [测试属性和事件与测试容器](../mfc/testing-properties-and-events-with-test-container.md)。  
  
     调整控件来显示您添加的所有按钮。  
  
2.  检查通过修改HTML插入的两个按钮。  每个按钮谨记在 [修改ATL DHTML控件](../atl/modifying-the-atl-dhtml-control.md)标识的标签: **Refresh** 和 **HelloHTML**。  
  
3.  测试两个新按钮以查看其工作方式。  
  
 现在测试不是用户界面的方法。  
  
1.  显示控件，因此，激活该边框。  
  
2.  在 **Control** 菜单上，单击 **Invoke Methods**。  
  
 在标记 **Method Name** 的列表的方法是容器可调用的方法: `MethodInvoked`和`GoToURL`。  其他方法由UI控件的。  
  
1.  选择一个方法调用并单击 `Invoke` 公开方法的消息框或定位到www.microsoft.com。  
  
2.  在 **Invoke Methods** 对话框中，单击 **Close**。  
  
 若要了解有关由一个ATL DHTML控件的各个组件和文件，请参见 [标识DHTML控件项目的元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md)。  
  
## 请参阅  
 [支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)