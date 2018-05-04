---
title: 封送处理 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2b8b82d5369aa536dab638efa379089325d10b1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="marshaling"></a>封送处理
封送处理的 COM 技术允许由一个进程，用于在另一个进程中的对象公开的接口。 封送处理、 COM 提供的代码 （或使用提供的接口实现的代码） 中进行打包到跨进程 （以及，通过在其他计算机上运行的进程电缆） 可以移动的格式的方法的参数并将这些参数解压缩在另一端。 同样，COM 必须从调用返回上执行相同的步骤。  
  
> [!NOTE]
>  封送处理时通常不需要与对象相同的进程中正在使用提供的对象的接口。 但是，封送处理可能需要在线程之间。  
  
## <a name="see-also"></a>请参阅  
 [COM 简介](../atl/introduction-to-com.md)   
 [封送处理的详细信息](http://msdn.microsoft.com/library/windows/desktop/ms692621)

