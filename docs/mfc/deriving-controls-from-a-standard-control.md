---
title: 从标准控件派生控件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50db9d4c99e8ef538ffaa5352f9ec96e5b08217f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="deriving-controls-from-a-standard-control"></a>从标准控件派生控件
与使用任何[CWnd](../mfc/reference/cwnd-class.md)-派生类，可以通过从现有控件类派生新类来修改控件的行为。  
  
### <a name="to-create-a-derived-control-class"></a>创建派生控件类  
  
1.  从现有控件类派生类，选择重写**创建**成员函数，以便它可以提供必需的自变量到基类**创建**函数。  
  
2.  提供消息处理程序成员函数和消息映射条目以修改控件行为来响应特定 Windows 消息。 请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。  
  
3.  提供新成员函数以扩展控件的功能（可选）。  
  
 在对话框中使用派生控件需要额外的工作。 对话框中的控件类型和位置一般是在对话框模板资源中指定的。 如果创建派生控件类，则无法在对话框模板中指定它，因为资源编译器不了解派生类。  
  
#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>在对话框中放置派生控件  
  
1.  在派生对话框类的声明中嵌入派生控件类的对象。  
  
2.  重写对话框类中的 `OnInitDialog` 成员函数以为派生控件调用 `SubclassDlgItem` 成员函数。  
  
 `SubclassDlgItem` 将通过对话框模板创建的类进行“动态子类化”。 当对某个控件进行动态子类化时，您将挂钩到 Windows，处理自己的应用程序中的一些消息，然后将其余的消息传入 Windows。 有关详细信息，请参阅[SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem)类的成员函数`CWnd`中*MFC 参考*。 以下示例演示如何编写 `OnInitDialog` 的重写来调用 `SubclassDlgItem`：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]  
  
 由于派生控件嵌入在对话框类中，因此将在构造对话框时构造该控件，将在销毁对话框时销毁该控件。 请将此代码中的示例比较[手动添加控件](../mfc/adding-controls-by-hand.md)。  
  
## <a name="see-also"></a>请参阅  
 [创建和使用控件](../mfc/making-and-using-controls.md)   
 [控件](../mfc/controls-mfc.md)

