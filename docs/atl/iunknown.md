---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IUnknown
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 760db28f4016ed529b45c72d25eaabf664642cd2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430038"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)是其他任何 COM 接口的基接口。  此接口定义三个方法： [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))， [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)，并[发行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)。 [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))允许界面用户向对象要求另一个其接口的指针。 [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)并[发行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)接口上实现引用计数。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[IUnknown 和接口继承](/windows/desktop/com/iunknown-and-interface-inheritance)

