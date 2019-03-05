---
title: 属性页
ms.date: 11/04/2016
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
ms.openlocfilehash: 0e335c20464d8ea71fd75ce2e67f67ca14edacb0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299317"
---
# <a name="implementing-property-pages"></a>属性页

属性页是 COM 对象实现`IPropertyPage`或`IPropertyPage2`接口。 ATL 提供支持，用于实现通过属性页[ATL 属性页向导](../atl/reference/atl-property-page-wizard.md)中[添加类对话框](../ide/add-class-dialog-box.md)。

若要创建使用 ATL 属性页：

- 创建或打开一个 ATL 动态链接库 (DLL) 的服务器项目。

- 打开[添加类对话框](../ide/add-class-dialog-box.md)，然后选择**ATL 属性页**。

- 请确保在属性页是单元线程 （因为它有一个用户界面）。

- 设置标题、 说明 （Doc 字符串） 和要与你的页面相关联的帮助文件。

- 将控件添加到生成的对话框资源，使其作为属性页的用户界面。

- 响应中页面的用户界面来执行验证、 更新页站点，或更新与你的页面相关联的对象的更改。 具体而言，调用[IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty)当用户在属性页中进行了更改。

- 选择重写`IPropertyPageImpl`方法使用以下指导原则。

   |IPropertyPageImpl 方法|重写时要...|说明|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|执行基本的完整性检查的对象传递给您的页面和它们支持的接口数量。|在调用基类实现之前执行你自己的代码。 如果要设置的对象不符合预期，应尽可能快地失败调用。|
   |[Activate](../atl/reference/ipropertypageimpl-class.md#activate)|初始化页面的用户界面 （例如，从对象中设置的当前属性值的对话框控件、 控件动态创建，或执行其他初始化）。|调用基类实现您的代码之前，因此，基本类有机会创建对话框窗口及其所有控件，然后再尝试将其更新。|
   |[Apply](../atl/reference/ipropertypageimpl-class.md#apply)|验证属性设置和更新的对象。|没有无需调用基类实现，因为它执行任何只跟踪调用。|
   |[停用](../atl/reference/ipropertypageimpl-class.md#deactivate)|清除与窗口相关的项。|基类实现都会破坏表示的属性页对话框。 如果需要清理销毁对话框之前，应调用基类之前添加代码。|

示例属性页的实现，请参阅[示例：实现属性页](../atl/example-implementing-a-property-page.md)。

> [!NOTE]
> 如果想要承载 ActiveX 控件属性页中，您需要更改您向导生成的类的派生。 替换**CDialogImpl\<CYourClass >** 与**CAxDialogImpl\<CYourClass >** 在基类列表中。

## <a name="see-also"></a>请参阅

[属性页](../atl/atl-com-property-pages.md)<br/>
[ATLPages 示例](../visual-cpp-samples.md)
