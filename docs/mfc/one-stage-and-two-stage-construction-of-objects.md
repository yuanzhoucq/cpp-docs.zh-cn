---
title: "对象的一阶段和两阶段构建 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 677a29d4f0b65a9490f24a5906d606a05bb4573b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>对象的一阶段和两阶段构建
你可以两种技术可用于创建图形对象，如钢笔和画笔选择：  
  
-   *一阶段构造*： 构造并初始化该对象在一个阶段中，所有使用构造函数。  
  
-   *两阶段构造*： 构造并初始化该对象在两个单独的阶段。 构造函数创建对象并初始化函数对其进行初始化。  
  
 两阶段构造始终是更安全的。 一阶段构造，如果你提供不正确的参数或内存分配失败，构造函数无法引发异常。 尽管你必须检查失败，将通过两阶段构造，避免该问题。 在任一情况下，销毁该对象是相同的进程。  
  
> [!NOTE]
>  这些技术适用于创建任何对象，而不只是图形对象。  
  
## <a name="example-of-both-construction-techniques"></a>这两种构造方法的示例  
 下面的简短示例演示构造 pen 对象的这两种方法：  
  
 [!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [图形对象](../mfc/graphic-objects.md)  
  
-   [将图形对象选入设备上下文](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [设备上下文](../mfc/device-contexts.md)  
  
-   [在视图中绘制](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>请参阅  
 [图形对象](../mfc/graphic-objects.md)

