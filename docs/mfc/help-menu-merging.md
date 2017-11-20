---
title: "帮助菜单合并 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 218493b6346858d33df042ec5754775272b1d788
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="help-menu-merging"></a>帮助菜单合并
菜单合并协议 OLE 文档容器中的活动对象时，使对象完成控制**帮助**菜单。 因此，容器的帮助主题将不可用，除非用户停用该对象。 活动文档包容体系结构基于就地菜单合并的规则进行扩展，以允许容器和活动文档共享此菜单。 新规则是一些有关哪些组件拥有菜单的哪个部分以及如何构造共享菜单的额外约定。  
  
 新约定很简单。 在活动文档中**帮助**菜单还拥有组织，如下所示的两个顶级菜单项：  
  
 `Help`  
  
 `Container Help >`  
  
 `Object Help    >`  
  
 例如，当 Word 部分中处于活动状态 Office 活页夹中，则**帮助**菜单会显示，如下所示：  
  
 `Help`  
  
 `Binder Help >`  
  
 `Word Help   >`  
  
 这两个菜单项都是级联菜单，其下方是特定于容器的任何附加菜单项和提供给用户的对象。 此处显示的项随容器和包含的对象而异。  
  
 若要构造此合并**帮助**菜单，活动文档包容体系结构可修改一般 OLE 文档过程。 根据 OLE 文档，合并的菜单栏可以有六个组的菜单，即**文件**，**编辑**，**容器**， `Object`，**窗口**，**帮助**按顺序。 每个组可包含零个或多个菜单。 组**文件**，**容器**，和**窗口**属于容器和组**编辑**，**对象、**和**帮助**属于的对象。 当对象需要执行菜单合并时，它会创建一个空白菜单栏并将其传递给容器。 容器然后插入其菜单中，通过调用**ioleinplaceframe:: Insertmenus**。 此对象还传递一个结构，它为 6 个 LONG 值数组 (**OLEMENUGROUPWIDTHS**)。 在插入菜单后，容器将标记它在每个组中添加的菜单数，然后返回。 然后，此对象插入其菜单，请注意每个容器组中的菜单计数。 最后，对象会将合并的菜单栏和数组（包含每个组中的菜单计数）传递给 OLE，后者将返回一个不透明的“菜单描述符”句柄。 更高版本的对象将传递该句柄和合并的菜单栏到容器中，通过**ioleinplaceframe:: Setmenu**。 此时，容器将显示合并后的菜单栏，并且还会将句柄传递给 OLE，以便 OLE 能够对菜单消息进行正确的调度。  
  
 在修改后的活动文档过程中，该对象必须先初始化**OLEMENUGROUPWIDTHS**到零，然后再将它传递给容器的元素。 然后，容器将执行常规菜单插入，有一个例外： 容器插入**帮助**菜单作为最后一项，并将值 1 存储中的最后一个 （第六个） 条目**OLEMENUGROUPWIDTHS**数组（即，宽度 [5]，属于对象的帮助组）。 这**帮助**菜单会有一个项，即子菜单，"**容器帮助**>"按前面所述的级联菜单。  
  
 对象将执行其常规菜单插入代码，但在将插入之前其**帮助**菜单上，它会检查的第六个条目**OLEMENUGROUPWIDTHS**数组。 如果值为 1，最后一个菜单的名称为**帮助**（或相应的本地化字符串），然后，此对象插入其**帮助**作为容器的子菜单的菜单**帮助**菜单。  
  
 该对象然后设置的第六个元素**OLEMENUGROUPWIDTHS**为零和第五个元素递增 1。 这可让 OLE 获知，**帮助**菜单属于容器，该菜单 （和及其子菜单） 对应的菜单消息应传送到该容器。 这样，就，容器负责转发`WM_INITMENUPOPUP`， **WM_SELECT**， **WM_COMMAND**，属于对象的一部分的其他菜单相关的消息和**帮助**菜单。 这通过使用实现`WM_INITMENU`清除通知容器是否在用户导航到对象的标志**帮助**菜单。 容器将监视`WM_MENUSELECT`进入或退出的任意项**帮助**容器未自行添加的菜单。 在进入时，这意味着用户已导航到某个对象菜单，以便容器设置"in object Help menu"标志，并使用该标志的状态转发任何`WM_MENUSELECT`， `WM_INITMENUPOPUP`，和**WM_COMMAND**消息，最少为对象窗口中。 （在退出时，容器将清除此标志，然后自行处理这些相同的消息。）容器应使用从对象的返回的窗口**ioleinplaceactiveobejct::**函数为目标，这些消息。  
  
 如果该对象会检测到的第六个元素中零**OLEMENUGROUPWIDTHS**，它将根据一般 OLE 文档规则继续进行。 此过程包含容器是否参与**帮助**菜单合并和一些不这样做。  
  
 当对象调用**ioleinplaceframe:: Setmenu**、 之前是否显示合并的菜单栏，容器将检查**帮助**菜单还拥有其他子菜单，除了容器具有插入。 如果，容器会使其**帮助**菜单合并的菜单栏中。 如果**帮助**菜单没有附加子菜单，容器将删除其**帮助**从合并的菜单栏的菜单。 此过程包含对象参与**帮助**菜单合并和一些不这样做。  
  
 最后，在开始反汇编菜单时，该对象会删除插入**帮助**除了删除其他插入的菜单菜单。 当容器删除其菜单时，它将删除其**帮助**除了插入该实体的其他菜单的菜单。  
  
## <a name="see-also"></a>另请参阅  
 [活动文档容器](../mfc/active-document-containers.md)

