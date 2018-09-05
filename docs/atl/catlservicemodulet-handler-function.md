---
title: 'Catlservicemodulet:: Handler 函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
dev_langs:
- C++
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbc7c74e0fd6fdd34ba9a0c386c028469113c88e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767074"
---
# <a name="catlservicemodulethandler-function"></a>Catlservicemodulet:: Handler 函数

`CAtlServiceModuleT::Handler` 是服务控制管理器 (SCM) 调用来检索服务的状态并为其提供各种说明 （如停止或暂停） 的例程。 SCM 将传递到一个操作代码`Handler`以指示服务应执行的操作。 默认 ATL 生成服务仅处理停止指令。 如果 SCM 通过 stop 指令，则服务将通知 SCM 程序即将停止。 然后，该服务调用`PostThreadMessage`来发送退出的消息到其自身。 这将终止消息循环，并最终将关闭该服务。

若要处理的详细说明，您需要更改`m_status`中的数据成员初始化`CAtlServiceModuleT`构造函数。 此数据成员通知 SCM 要启用服务控制面板应用程序中选择该服务时的按钮。

## <a name="see-also"></a>请参阅

[服务](../atl/atl-services.md)   
[Catlservicemodulet:: Handler](../atl/reference/catlservicemodulet-class.md#handler)

