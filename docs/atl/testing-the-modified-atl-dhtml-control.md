---
title: 测试已修改的 ATL DHTML 控件
ms.date: 11/06/2018
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
ms.openlocfilehash: 55cdaba64ccb95ee5695c082a5e146b1e7dc2cf3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277230"
---
# <a name="testing-the-modified-atl-dhtml-control"></a>测试已修改的 ATL DHTML 控件

试用新控件，以确定其工作原理现在。

## <a name="to-build-and-test-the-modified-control"></a>若要生成和测试修改后的控件

1. 重新生成项目并将其在中打开**测试容器**。 请参阅[使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)有关如何访问的信息**测试容器**。

   调整要显示所有您添加的按钮的控件的大小。

1. 检查由更改 HTML 插入的两个按钮。 每个按钮具有中标识的标签[修改 ATL DHTML 控件](../atl/modifying-the-atl-dhtml-control.md):**刷新**并**HelloHTML**。

1. 测试两个新的按钮，以查看它们的工作原理。

现在，测试不是用户界面的一部分的方法。

1. 突出显示该控件，因此激活边框。

1. 上**控制**菜单中，选择**调用方法**。

   在列表中标记为方法**方法名称**是容器可以调用的方法：`MethodInvoked`和`GoToURL`。 通过用户界面控制所有其他方法。

1. 选择一种方法来调用并选择**Invoke**显示方法的消息框，或导航到`www.microsoft.com`。

1. 在中**调用方法**对话框框中，选择**关闭**。

若要了解有关的各种元素和构成 ATL DHTML 控件文件的详细信息，请参阅[标识 DHTML 控件项目的元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md)。

## <a name="see-also"></a>请参阅

[支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)
