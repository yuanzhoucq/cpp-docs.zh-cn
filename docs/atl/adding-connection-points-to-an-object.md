---
title: "将连接点添加到对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f63ec5bd9029302192e640e42a3d012df347219d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-connection-points-to-an-object"></a>将连接点添加到对象
[ATL 教程](../atl/active-template-library-atl-tutorial.md)演示如何创建与连接点支持的控件、 如何添加事件，以及如何实现连接点。 ATL 实现连接点与[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)类。  
  
 若要实现连接点，你有两个选择：  
  
-   实现你自己传出的事件源，通过将连接点添加到控件或对象。  
  
-   重复使用另一个类型库中定义的连接点接口。  
  
 在任一情况下，实现连接点向导使用类型库来完成其工作。  
  
### <a name="to-add-a-connection-point-to-a-control-or-object"></a>若要添加的控件或对象的连接点  
  
1.  在.idl 文件的库块中定义的调度接口。 如果你启用连接点支持使用 ATL 控件向导创建控件时，将已创建调度接口。 如果你未启用连接点支持你在创建控件时，必须手动将调度接口添加到.idl 文件中。 下面是调度接口的示例。 输出接口不是需要调度接口，但如 VBScript 和 JScript 的许多脚本语言要求执行此操作，因此本示例使用两个支持：  
  
     [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]  
  
     使用 uuidgen.exe 或 guidgen.exe 实用工具以生成 GUID。  
  
2.  添加作为调度接口`[default,source]`中项目的.idl 文件中的对象的组件类的接口。 同样，如果你在创建控件时启用连接点的支持，ATL 控件向导将创建`[default,source`] 条目。 若要手动添加此项，请以粗体显示添加行：  
  
     [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]  
  
     请参阅中的.idl 文件[Circ](../visual-cpp-samples.md)有关示例的 ATL 示例。  
  
3.  使用类视图将方法和属性添加到事件接口。 右键单击类视图中的类，指向**添加**快捷菜单，然后单击**添加连接点**。  
  
4.  在**源接口**实现连接点向导中，选择列表框**项目的接口**。 如果你选择用于你的控件和按的接口**确定**，你将：  
  
    -   生成事件代理类中实现的代码，将进行传出调用事件的标头文件。  
  
    -   将条目添加到连接点图。  
  
     此外会在你的计算机上所有的类型库的列表。 你只应使用这些其他类型库之一定义你的连接点，如果你想要实现完全相同传出的接口在另一个类型库中找到。  
  
### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>若要重用的连接点接口定义另一个类型库中  
  
1.  在类视图中，右键单击一个类以实现**BEGIN_COM_MAP**宏，指向**添加**快捷菜单，然后单击**添加连接点**。  
  
2.  在实现连接点向导中，选择在类型库中的类型库和接口，然后单击**添加**。  
  
3.  编辑.idl 文件为：  
  
    -   从正在使用其事件源的对象的.idl 文件复制调度接口。  
  
    -   使用**importlib**该类型库的说明。  
  
## <a name="see-also"></a>请参阅  
 [连接点](../atl/atl-connection-points.md)

