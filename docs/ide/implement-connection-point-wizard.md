---
title: 实现连接点向导
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.impl.cp.overview
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
ms.openlocfilehash: b818a1a149e95805a8694f6c8d8d1325b33211b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531529"
---
# <a name="implement-connection-point-wizard"></a>实现连接点向导

本向导实现 COM 对象的连接点。 可连接对象（即，源）可以为其自身接口或任何传出接口公开连接点。 Visual C++ 和 Windows 都提供具有传出接口的类型库。 每个传出接口都可以由对象（即，接收器）上的客户端实现。

有关详细信息，请参阅 [ATL 连接点](../atl/atl-connection-points.md)。

- **可用类型库**

   显示包含可实现接口点的接口定义的可用类型库。 单击省略号按钮，找到包含要使用的类型库的文件。

- **位置**

   显示“可用类型库”列表中当前选择的类型库的位置。

- **接口**

   显示其定义包含在“可用类型库”框中当前选定的类型库中的接口。

   |传输按钮|描述|
   |---------------------|-----------------|
   |**>**|将当前在“接口”列表中选择的接口名称添加到“实现连接点”列表中。|
   |**>>**|将在“接口”列表中可用的所有接口名称添加到“实现连接点”列表中。|
   |**\<**|删除当前在“实现连接点”列表中所选的接口名称。|
   |**\<\<**|删除当前在“实现连接点”列表中列出的所有接口名称。|

- **实现连接点**

   单击“完成”时显示实现其连接点的接口的名称。

## <a name="see-also"></a>请参阅

[实现连接点](../ide/implementing-a-connection-point-visual-cpp.md)