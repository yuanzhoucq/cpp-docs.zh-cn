---
title: 测试 ATL DHTML 控件
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls
- DHTML controls, testing
ms.assetid: 0e4b4358-80ce-4505-8b06-ef4f30b1d1f0
ms.openlocfilehash: e808a21fe890db6e711bc66adf02b3e71f801dba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522520"
---
# <a name="testing-the-atl-dhtml-control"></a>测试 ATL DHTML 控件

创建项目后，可以生成和测试示例控件。 执行此操作之前，请使用**类视图**并**解决方案资源管理器**若要检查的项目。 中更详细地介绍了你的项目的元素[标识 DHTML 控件项目的元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md)。

## <a name="to-build-and-test-the-atl-dhtml-control"></a>若要生成和测试 ATL DHTML 控件

1. 生成项目。 从**构建**菜单上，单击**生成解决方案**。

1. 生成完成后，打开**测试容器**。 请参阅[使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)有关如何访问的信息**测试容器**。

1. 在中**测试容器**，从**编辑**菜单中，单击**插入新控件**。

1. 在中**插入控件**对话框框中，从列表框中选择您的控件。 请记住，其名称基于 ATL 控件向导中指示的短名称。 单击 **“确定”**。

1. 检查该控件。 请注意，它包含滚动条。 使用控件的句柄来调整控件以激活滚动条的大小。

1. 测试控件的按钮。 背景色更改为指示按钮的颜色。

1. 关闭**测试容器**。

接下来，请尝试[修改 DHTML 控件](../atl/modifying-the-atl-dhtml-control.md)。

## <a name="see-also"></a>请参阅

[支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)
