---
title: 实现接口
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.interface.overview
helpviewer_keywords:
- interfaces, implementing
- implement interface wizard [C++]
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: bb1db35e269ef884f3ebdf4564d8f0a3e579db50
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509510"
---
# <a name="implement-an-interface"></a>实现接口

要实现接口，必须将项目创建为 ATL COM 应用程序或包含 ATL 支持的 MFC 应用程序。 可使用 [ATL 项目向导](../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或[将 ATL 对象添加到 MFC 应用程序](../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现对 MFC 应用程序的 ATL 支持。

创建项目后，要实现接口，必须首先添加 ATL 对象。 有关将对象添加到 ATL 项目的向导列表，请参阅[将对象和控件添加到 ATL 项目](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。

> [!NOTE]
> 向导不支持 ATL 对话框、使用 ATL 的 XML Web 服务、性能对象或性能计数器。

如果[添加 ATL 控件](../atl/reference/adding-an-atl-control.md)，则可以指定是否实现默认接口。 默认接口列在该向导的[接口](../atl/reference/interfaces-atl-control-wizard.md)页上，并在 atlcom.h 中定义。

添加对象或控件后，可使用实现接口向导来实现位于任何可用类型库中的其他接口。

如果要添加新接口，则必须手动将其添加到项目的 .idl 文件中。 有关详细信息，请参阅[在 ATL 项目中添加新接口](../atl/reference/adding-a-new-interface-in-an-atl-project.md)。

**实现接口：**

1. 在类视图中，右键单击 ATL 对象的类名。

1. 选择快捷菜单中的“添加”，然后选择“实现接口”以显示[实现接口向导](#implement-interface-wizard)   。

1. 从适当的类型库中选择要实现的接口，然后选择“完成”  。

1. 在“类视图”中，展开对象的“基础和接口”节点以查看已实现的接口。 然后展开接口的节点以查看其可用的属性、方法和事件。

   > [!NOTE]
   > 还可使用[对象浏览器](/visualstudio/ide/viewing-the-structure-of-code)检查接口的成员。

## <a name="in-this-section"></a>本节内容

- [实现接口向导](#implement-interface-wizard)

## <a name="implement-interface-wizard"></a>实现接口向导

本向导实现 COM 对象的接口。 Visual Studio 和 Windows 提供的 COM 库中包含许多接口的实现。 创建某个对象的实例时，接口实现即与该对象相关联。 它还提供该对象提供的服务。

有关接口和实现的讨论，请参阅 Windows SDK 中的[接口和接口实现](/windows/win32/com/interfaces-and-interface-implementations)。

- **实现接口的位置**

  指定从中创建接口的类型库的位置。

  |选项|说明|
  |------------|-----------------|
  |**Project**|类型库是项目的一部分。|
  |**Registry**|在系统中注册类型库。 “可用类型库”中列出了已注册的类型库  。|
  |**文件**|类型库不必在系统中注册，但必须包含在文件中。 在“位置”中提供文件位置  。|

- **可用类型库**

  显示包含可实现的接口定义的可用类型库。 如果在“实现接口的位置”下选择“文件”，则此框无法更改   。

- **位置**

  显示“可用类型库”列表中当前选择的类型库的位置  。 如果在“实现接口的位置”下选择了“文件”，请选择省略号按钮以找到包含要使用的类型库的文件   。

- **接口**

  显示其定义包含在“可用类型库”框中当前选定的类型库中的接口  。

  > [!NOTE]
  > “接口”框中不显示与选定对象已实现的接口同名的接口  。

  |传输按钮|说明|
  |---------------------|-----------------|
  |**>**|将当前在“接口”列表中选择的接口名称添加到“实现接口”列表中   。|
  |**>>**|将“接口”列表中可用的所有接口名称添加到“实现接口”列表中   。|
  |**\<**|删除当前在“实现接口”列表中所选的接口名称  。|
  |**\<\<**|删除当前在“实现接口”列表中列出的所有接口名称  。|

- **实现接口**

  显示已选择在对象上实现的接口名称。

  > [!NOTE]
  > 如果包含从 `IDispatch` 派生的多个接口，或者尝试实现从类中已有的另一个接口派生的接口，则必须消除 COM_MAP 项的歧义。 有关详细信息，请参阅 [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2)。
