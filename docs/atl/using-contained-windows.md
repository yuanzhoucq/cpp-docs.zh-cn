---
title: 使用包含的 Windows |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6c3b439baf05c4e4287613e9b6b5a9b1c2546b6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="using-contained-windows"></a>使用包含的窗口
ATL 实现与包含的 windows [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)。 包含的窗口表示消息委托给容器对象而不是其自己的类中处理它们的窗口。  
  
> [!NOTE]
>  不需要从派生类`CContainedWindowT`若要使用包含的窗口。  
  
 包含的窗口，你可以使用任一超类现有的 Windows 类或子类化现有窗口。 若要创建该超类现有的 Windows 的窗口类中，首先的构造函数中指定现有的类名称`CContainedWindowT`对象。 然后调用`CContainedWindowT::Create`。 不需要在现有的窗口子类化，请指定 Windows 类名称 (传递**NULL**给构造函数)。 只需调用`CContainedWindowT::SubclassWindow`与正在子类化窗口的句柄的方法。  
  
 通常情况下，为数据类成员的容器需要使用包含的窗口。 容器不需要是窗口;但是，它必须派生自[CMessageMap](../atl/reference/cmessagemap-class.md)。  
  
 所包含可以使用备用的消息映射来处理其消息。 如果你有多个包含的窗口，你应声明多个替换消息映射，每个对应于单独的包含窗口。  
  
## <a name="example"></a>示例  
 以下是具有两个包含 windows 的容器类的一个示例：  
  
 [!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]  
  
 有关包含的窗口的详细信息，请参阅[SUBEDIT](../visual-cpp-samples.md)示例。  
  
## <a name="see-also"></a>请参阅  
 [窗口类](../atl/atl-window-classes.md)

