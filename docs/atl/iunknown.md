---
title: IUnknown |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5903cebe5de87ab528dbcfe1769047b7b7ace3ef
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761909"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)是其他任何 COM 接口的基接口。  此接口定义三个方法： [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))， [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)，并[发行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)。 [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))允许界面用户向对象要求另一个其接口的指针。 [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)并[发行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)接口上实现引用计数。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)   
[IUnknown 和接口继承](/windows/desktop/com/iunknown-and-interface-inheritance)

