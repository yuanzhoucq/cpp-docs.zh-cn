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
ms.openlocfilehash: d832d2978bf9db82b290d77b236fea1c9bcada58
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953037"
---
# <a name="iunknown"></a>IUnknown
[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)是其他任何 COM 接口的基接口。  此接口定义三个方法： [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)， [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)，并[发行](http://msdn.microsoft.com/library/windows/desktop/ms682317)。 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)允许界面用户向对象要求另一个其接口的指针。 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)并[发行](http://msdn.microsoft.com/library/windows/desktop/ms682317)接口上实现引用计数。  
  
## <a name="see-also"></a>请参阅  
 [COM 简介](../atl/introduction-to-com.md)   
 [IUnknown 和接口继承](http://msdn.microsoft.com/library/windows/desktop/ms692713)

