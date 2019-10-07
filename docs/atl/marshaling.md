---
title: 封送
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 9963e261f26daa57cb58e30ffc404b431d781bfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492046"
---
# <a name="marshaling"></a>封送

封送的 COM 方法允许在一个进程中使用对象公开的接口, 以便在另一个进程中使用。 在封送处理中, COM 提供代码 (或使用接口实现器提供的代码), 将方法的参数打包为可跨进程移动的格式 (以及跨网络移动到其他计算机上运行的进程) 并解包这些参数另一端。 同样, COM 必须在从调用返回时执行相同的步骤。

> [!NOTE]
>  当对象提供的接口与对象在同一进程中使用时, 通常不需要封送处理。 但是, 线程之间可能需要封送处理。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[封送详细信息](/windows/win32/com/marshaling-details)
