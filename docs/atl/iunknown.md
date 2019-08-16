---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 9c9faa4cffcdc8e6840dfbbe141cb63f51155ded
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492062"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)是每个其他 COM 接口的基接口。  此接口定义三种方法:[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))、 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)。 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))允许接口用户要求对象指向其接口的另一个接口。 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)在接口上实现引用计数。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[IUnknown 和接口继承](/windows/win32/com/iunknown-and-interface-inheritance)
