---
title: "ATL 项目中添加新接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 8e4916c60310dd8dcbf0bb9e8c1f151309a32621
ms.lasthandoff: 02/24/2017

---
# <a name="adding-a-new-interface-in-an-atl-project"></a>ATL 项目中添加新接口
将接口添加到您的对象或控件，您同时也在该接口中创建无存根函数为每个方法。 在您的对象或控件，可以添加只有当前在现有类型库中找到的接口。 此外，在其中添加该接口的类必须实现[BEGIN_COM_MAP](http://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333)宏或，如果项目属性化，它必须具有`coclass`属性。  
  
 您可以向控件中两种方式之一添加新接口︰ 手动或者类视图中使用代码向导。  
  
### <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>若要在类视图中使用代码向导将接口添加到现有对象或控件  
  
1.  在[类视图](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，用鼠标右键单击控件的类名称。 例如，完全控制或复合控件或在其标头文件中实现 BEGIN_COM_MAP 宏的任何其他控件类。  
  
2.  在快捷菜单上，单击**添加**，然后单击**实现接口**。  
  
3.  选择要在中实现的接口[实现接口向导](../../ide/implement-interface-wizard.md)。 如果任何可用的类型库中不存在该接口，然后您必须将其添加手动到.idl 文件。  
  
### <a name="to-add-a-new-interface-manually"></a>若要手动添加新接口  
  
1.  将新接口的定义添加到.idl 文件。  
  
2.  派生您的对象或从界面的控件。  
  
3.  创建一个新[COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/c5363b8b-a1a2-471e-ad3a-d472f6c356c5)的接口，或者如果项目属性化，将添加`coclass`属性。  
  
4.  在接口上实现方法。  
  
## <a name="see-also"></a>另请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [Visual c + + 项目类型](../../ide/visual-cpp-project-types.md)   
 [使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)


