---
title: ATL 项目中添加一个新接口 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.interface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2c9d0ef4c14760d596a4aa26fa2a929da26c67b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>ATL 项目中添加一个新接口
将接口添加到你的对象或控件时，将在该接口创建每个方法的存根处理扩展函数。 在你的对象或控件，可以添加仅将接口当前在现有的类型库中找到。 此外，在其中添加接口的类必须实现[BEGIN_COM_MAP](com-map-macros.md#begin_com_map)宏或如果项目属性化，则它必须`coclass`属性。  
  
 可以将新接口添加到您在两种方式之一中的控件： 手动或在类视图中使用代码向导。  
  
### <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>若要在类视图中使用代码向导将接口添加到现有对象或控件  
  
1.  在[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，右键单击控件的类名称。 例如，完全控制或复合控件或在其标头文件中实现 BEGIN_COM_MAP 宏的任何其他控件类。  
  
2.  在快捷菜单上，单击**添加**，然后单击**实现接口**。  
  
3.  选择要在中实现的接口[实现接口向导](../../ide/implement-interface-wizard.md)。 如果接口不存在任何可用的类型库中，然后你必须手动添加它到.idl 文件。  
  
### <a name="to-add-a-new-interface-manually"></a>若要手动添加新接口  
  
1.  将新接口的定义添加到.idl 文件。  
  
2.  派生对象或从界面的控件。  
  
3.  创建一个新[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)接口或者，如果项目属性化，将添加`coclass`属性。  
  
4.  在接口上实现方法。  
  
## <a name="see-also"></a>请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [Visual c + + 项目类型](../../ide/visual-cpp-project-types.md)   
 [使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 运行时代码编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

