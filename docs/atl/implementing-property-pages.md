---
title: 实现属性页 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1db6ca4ea374cd76d5b0e1df8e6c0cd03474fdf2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-property-pages"></a>实现的属性页
属性页是 COM 对象实现`IPropertyPage`或**IPropertyPage2**接口。 ATL 为实现通过属性页提供支持[ATL 属性页向导](../atl/reference/atl-property-page-wizard.md)中[添加类对话框](../ide/add-class-dialog-box.md)。  
  
 若要创建使用 ATL 属性页：  
  
-   创建或打开一个 ATL 动态链接库 (DLL) 的服务器项目。  
  
-   打开[添加类对话框](../ide/add-class-dialog-box.md)和选择**ATL 属性页**。  
  
-   请确保属性页单元线程 （因为它具有用户界面）。  
  
-   设置标题、 说明 （Doc 字符串） 和要与你的页面相关联的帮助文件。  
  
-   将控件添加到生成的对话框资源，使其作为属性页的用户界面。  
  
-   响应中页面的用户界面来执行验证、 更新页站点，或更新与你的页面关联的对象的更改。 具体而言，调用[IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)当用户在属性页中进行了更改。  
  
-   （可选） 重写`IPropertyPageImpl`方法使用以下指导原则。  
  
    |IPropertyPageImpl 方法|重写时要...|说明|  
    |------------------------------|----------------------------------|-----------|  
    |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|对进行基本的完整性检查传递给你的页面和它们支持的接口的对象数。|在调用基类实现前执行你自己的代码。 如果要设置的对象不符合你的期望，应尽快失败调用。|  
    |[激活](../atl/reference/ipropertypageimpl-class.md#activate)|初始化页面的用户界面 （例如，从对象设置的当前属性值的对话框控件，动态创建控件，或执行其他初始化）。|调用基类实现您的代码之前，因此，基类有可能创建对话框窗口和所有控件之前尝试更新它们。|  
    |[应用](../atl/reference/ipropertypageimpl-class.md#apply)|验证的属性设置，需要更新的对象。|没有无需调用基类实现，因为它执行任何操作只跟踪调用。|  
    |[停用](../atl/reference/ipropertypageimpl-class.md#deactivate)|清除窗口相关项。|基类实现销毁表示的属性页对话框。 如果你需要清理销毁对话框之前，应调用基类之前添加你的代码。|  
  
 有关示例属性页的实现，请参阅[示例： 实现属性页](../atl/example-implementing-a-property-page.md)。  
  
> [!NOTE]
>  如果你想托管 ActiveX 控件属性页中，你将需要更改你向导生成的类派生。 替换**CDialogImpl\<CYourClass >** 与**CAxDialogImpl\<CYourClass >** 基类列表中。  
  
## <a name="see-also"></a>请参阅  
 [属性页](../atl/atl-com-property-pages.md)   
 [ATLPages 示例](../visual-cpp-samples.md)

