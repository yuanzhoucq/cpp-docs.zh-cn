---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 17561092c6cccbad264bb82d68dbef9c0e078f76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250279"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)是其他任何 COM 接口的基接口。  此接口定义三个方法：[QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))， [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)，和[发行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)。 [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))允许界面用户向对象要求另一个其接口的指针。 [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)并[发行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)接口上实现引用计数。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[IUnknown 和接口继承](/windows/desktop/com/iunknown-and-interface-inheritance)
