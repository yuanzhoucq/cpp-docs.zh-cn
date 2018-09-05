---
title: 测试 ATL DHTML 控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls
- DHTML controls, testing
ms.assetid: 0e4b4358-80ce-4505-8b06-ef4f30b1d1f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be4bb44455fb97a61cb4af608667bd5c05f2756a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766287"
---
# <a name="testing-the-atl-dhtml-control"></a>测试 ATL DHTML 控件

创建项目后，可以生成和测试示例控件。 执行此操作之前，请使用类视图和解决方案资源管理器检查的项目。 中更详细地介绍了你的项目的元素[标识 DHTML 控件项目的元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md)。

#### <a name="to-build-and-test-the-atl-dhtml-control"></a>若要生成和测试 ATL DHTML 控件

1. 生成项目。 从**构建**菜单上，单击**生成解决方案**。

2. 生成完成后，打开测试容器。 请参阅[使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)有关如何访问测试容器的信息。

3. 在测试容器中，从**编辑**菜单上，单击**插入新控件**。

4. 在中**插入控件**对话框框中，从列表框中选择您的控件。 请记住，其名称基于 ATL 控件向导中指示的短名称。 单击 **“确定”**。

5. 检查该控件。 请注意，它包含滚动条。 使用控件的句柄来调整控件以激活滚动条的大小。

6. 测试控件的按钮。 背景色更改为指示按钮的颜色。

7. 关闭测试容器。

接下来，请尝试[修改 DHTML 控件](../atl/modifying-the-atl-dhtml-control.md)。

## <a name="see-also"></a>请参阅

[支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)

