---
title: 在 ATL 项目中添加新接口 |Microsoft Docs
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
ms.openlocfilehash: fec98fd785f5e99875c5f73b13ce1082c16add2b
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861754"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>在 ATL 项目中添加新接口

当将接口添加到对象或控件时，该接口中创建无存根函数为每个方法。 在您的对象或控件，可以添加仅当前在现有类型库中找到的接口。 此外，在其中添加了接口的类必须实现[BEGIN_COM_MAP](com-map-macros.md#begin_com_map)宏或，如果项目属性化，它必须具有`coclass`属性。

可以向控件中的两种方式之一添加新的接口： 手动或在类视图中使用代码向导。

## <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>若要在类视图中使用代码向导将接口添加到现有对象或控件

1. 在中[类视图](/visualstudio/ide/viewing-the-structure-of-code)，右键单击一个控件的类名。 例如，完全控制或复合控件或在其标头文件中实现 BEGIN_COM_MAP 宏的任何其他控件类。

1. 在快捷菜单上，单击**外**，然后单击**实现接口**。

1. 选择要在中实现的接口[实现接口向导](../../ide/implement-interface-wizard.md)。 如果接口不存在任何可用的类型库中，然后你必须将其添加手动到.idl 文件。

## <a name="to-add-a-new-interface-manually"></a>若要手动添加新接口

1. 将新接口的定义添加到.idl 文件。

1. 派生对象或从接口的控件。

1. 创建一个新[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)接口或者，如果项目属性化，添加`coclass`属性。

1. 该接口上实现方法。

## <a name="see-also"></a>请参阅

[ATL 项目向导](../../atl/reference/atl-project-wizard.md)<br/>
[Visual C++ 项目类型](../../ide/visual-cpp-project-types.md)<br/>
[使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)
