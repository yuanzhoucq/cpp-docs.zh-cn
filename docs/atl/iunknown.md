---
title: "IUnknown |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IUnknown
dev_langs: C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f750cea17029a76f56edaa3dc6531554fa81901a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="iunknown"></a>IUnknown
[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)是每个其他 COM 接口的基接口。  此接口定义三个方法： [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)， [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)，和[版本](http://msdn.microsoft.com/library/windows/desktop/ms682317)。 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)允许接口用户寻求指向另一个其接口的指针的对象。 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)和[版本](http://msdn.microsoft.com/library/windows/desktop/ms682317)实现引用计数的接口上。  
  
## <a name="see-also"></a>另请参阅  
 [COM 简介](../atl/introduction-to-com.md)   
 [IUnknown 和接口继承](http://msdn.microsoft.com/library/windows/desktop/ms692713)

