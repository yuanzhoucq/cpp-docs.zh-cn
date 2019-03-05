---
title: COM + 1.0 支持在 ATL 项目中
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.MTS
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
ms.openlocfilehash: 39a3597b8df833d89942e31b361f791b14ceb8c9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292586"
---
# <a name="com-10-support-in-atl-projects"></a>COM + 1.0 支持在 ATL 项目中

可以使用[ATL 项目向导](../../atl/reference/creating-an-atl-project.md)具有基本支持的 COM + 1.0 组件创建的项目。

COM + 1.0 专为开发的基于组件的分布式应用程序。 它还提供用于部署和管理这些应用程序的运行时基础结构。

如果选择**支持 COM + 1.0**复选框，向导将修改在链接步骤的生成脚本。 具体而言，COM + 1.0 项目链接到以下库：

- comsvcs.lib

- Mtxguid.lib

如果选择**支持 COM + 1.0**复选框，您还可以选择**支持组件注册机构**。 组件注册器使您的 COM + 1.0 对象来获取一系列组件、 注册组件，或 （单独或全部同时） 撤消注册组件。

## <a name="see-also"></a>请参阅

[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)
