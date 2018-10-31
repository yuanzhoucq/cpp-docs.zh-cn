---
title: 将连接点添加到对象 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 685f1b7d24e781dbee6d67b325b059f09ca9bf4c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054210"
---
# <a name="adding-connection-points-to-an-object"></a>将连接点添加到对象

[ATL 教程](../atl/active-template-library-atl-tutorial.md)演示如何创建连接点支持控件、 如何添加事件，以及如何实现连接点。 ATL 实现连接点[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)类。

若要实现连接点，您有两种选择：

- 通过将连接点添加到控件或对象来实现您自己传出的事件源。

- 重复使用另一个类型库中定义的连接点接口。

在任一情况下，实现连接点向导使用类型库来完成其工作。

### <a name="to-add-a-connection-point-to-a-control-or-object"></a>若要添加到控件或对象的连接点

1. 定义.idl 文件的库块中的调度接口。 如果您启用了对连接点，使用 ATL 控件向导创建控件时，将已创建调度接口。 如果您不启用支持连接点的创建控件时，必须手动将调度接口添加到.idl 文件中。 下面是调度接口的示例。 传出接口不需要为调度接口，但许多脚本编写语言，如 VBScript 和 JScript 需要此操作，因此此示例使用两个调度接口：

   [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]

   使用 uuidgen.exe 或 guidgen.exe 实用程序生成的 GUID。

2. 添加作为调度接口`[default,source]`中项目的.idl 文件中的对象的组件类的接口。 同样，如果你在创建控件时启用对连接点的支持，ATL 控件向导将创建`[default,source`] 条目。 若要手动添加此项，添加以粗体显示的行：

   [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]

   请参阅中的.idl 文件[Circ](../visual-cpp-samples.md) ATL 示例有关的示例。

3. 使用类视图将方法和属性添加到事件接口。 右键单击类视图中的类，指向**外**快捷菜单，然后单击**添加连接点**。

4. 在中**源接口**的实现连接点向导，选择列表框**项目的接口**。 如果您选择的接口控制并按**确定**，你将：

   - 生成具有事件代理类实现的代码，将进行传出调用的事件的标头文件。

   - 连接点映射到添加一个条目。

   此外会在计算机上所有的类型库的列表。 仅应使用这些其他类型库之一来定义连接点，如果你想要实现在另一个类型库中找到的完全相同的输出接口。

### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>若要重复使用连接点接口中定义另一个类型库

1. 在类视图中，右键单击实现的类**BEGIN_COM_MAP**宏，依次指向**添加**快捷菜单，然后单击**添加连接点**。

2. 在实现连接点向导中，选择类型库中的类型库和一个接口并单击**添加**。

3. 编辑为.idl 文件：

   - 将从其事件源正在使用的对象的.idl 文件复制调度接口。

   - 使用**importlib**该类型库的说明。

## <a name="see-also"></a>请参阅

[连接点](../atl/atl-connection-points.md)

