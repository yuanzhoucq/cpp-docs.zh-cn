---
title: 双重接口和事件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99dc173f3dde8ea81f6dc11d02298cd94673f999
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354062"
---
# <a name="dual-interfaces-and-events"></a>双重接口和事件
可以设计作为一个双的事件接口时，有多种良好的设计原因不要这样做。 基本的原因是事件源将仅触发事件通过 vtable 或`Invoke`，而不是同时。 如果事件源触发作为直接 vtable 方法调用，事件`IDispatch`永远不会使用方法和很明显的接口应已纯 vtable 接口。 如果事件源触发事件时为对的调用`Invoke`将永远不会使用 vtable 方法，它是清除接口应已调度接口。 如果您定义事件接口为双重接口，则你将要求客户端实现将永远不会使用接口的一部分。  
  
> [!NOTE]
>  此参数不适用于双重接口，一般情况下。 从实现的角度看，双重接口是实现广泛的客户端可以访问的接口的快速、 便利，然而和广受支持的方式。  
  
 进一步有原因，若要避免双事件接口;Visual Basic 和 Internet Explorer 都不支持这些选项。  
  
## <a name="see-also"></a>请参阅  
 [双重接口和 ATL](../atl/dual-interfaces-and-atl.md)

