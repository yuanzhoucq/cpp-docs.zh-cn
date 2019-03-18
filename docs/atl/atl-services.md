---
title: ATL 服务
ms.date: 11/04/2016
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
ms.openlocfilehash: 052169154a62cbd07a82f08087fc2c2db8ae46c5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819052"
---
# <a name="atl-services"></a>ATL 服务

若要创建您的 ATL COM 对象，以便使其在服务中运行，只需从 ATL 项目向导中的服务器选项的列表中选择服务 (EXE)。 然后，向导将创建派生自的类`CAtlServiceModuleT`来实现该服务。

为服务生成后的 ATL COM 对象，它仅将注册为本地服务器和它不会出现在控制面板中的服务列表。 这是因为它是更轻松地调试不作为服务的本地服务器的服务。 若要安装它作为一项服务，在命令提示符处运行以下命令：

`YourEXE` `.exe /Service`

若要卸载它，请运行以下命令：

`YourEXE` `.exe /UnregServer`

在本部分中的前四个主题讨论的执行过程中发生的操作`CAtlServiceModuleT`成员函数。 这些主题出现在相同的序列，因为通常调用的函数。 若要提高您对这些主题的理解，它是使用源代码作为参考 ATL 项目向导生成的一个好办法。 这些前四个主题是：

- [Catlservicemodulet:: Start 函数](../atl/reference/catlservicemodulet-class.md#start)

- [Catlservicemodulet:: Servicemain 函数](../atl/reference/catlservicemodulet-class.md#servicemain)

- [Catlservicemodulet:: Run 函数](../atl/reference/catlservicemodulet-class.md#run)

- [Catlservicemodulet:: Handler 函数](../atl/reference/catlservicemodulet-class.md#handler)

最后三个主题讨论了与开发服务相关的概念：

- [注册表项](../atl/registry-entries.md)ATL 服务

- [DCOMCNFG](../atl/dcomcnfg.md)

- [调试提示](../atl/debugging-tips.md)ATL 服务

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)
