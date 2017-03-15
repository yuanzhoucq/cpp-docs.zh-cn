---
title: "Implementing Property Pages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPropertyPage class"
  - "IPropertyPage2 class"
  - "属性页, 实现"
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Implementing Property Pages
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

属性页是实现 `IPropertyPage` 或 **IPropertyPage2** 接口的COM对象。  ATL提供实现属性页支持通过在 [添加选件类对话框](../ide/add-class-dialog-box.md)的 [ATL属性页向导](../atl/reference/atl-property-page-wizard.md)。  
  
 使用ATL，创建属性页:  
  
-   创建或打开一个ATL动态链接库\(DLL\)服务器项目。  
  
-   打开 [添加选件类对话框](../ide/add-class-dialog-box.md) 并选择 **ATL Property Page**。  
  
-   确定您的属性页是线程单元中\(因为它具有用户界面）。  
  
-   将关联的标题、说明\(文档字符串\)和帮助文件与您的网页。  
  
-   将控件添加到生成的对话框资源作为属性页用户界面。  
  
-   响应在页的用户界面中的更改执行验证，更新页面网站或更新对象与您的网页。  特别是，那么，当用户对属性页时，的更改调用 [IPropertyPageImpl::SetDirty](../Topic/IPropertyPageImpl::SetDirty.md)。  
  
-   可以选择重写 `IPropertyPageImpl` 方法使用下面的准则。  
  
    |IPropertyPageImpl方法|重写，当希望…|注释|  
    |-------------------------|-------------|--------|  
    |[SetObjects](../Topic/IPropertyPageImpl::SetObjects.md)|执行在传递给它们支持的页面和接口的对象数目的基本完全检查。|在调用基类实现之前执行代码。  如果设置的对象不符合您的预期相符，应尽快失败调用。|  
    |[激活](../Topic/IPropertyPageImpl::Activate.md)|初始化使用页的用户界面\(例如，设置与当前属性值的对话框控件从对象，动态创建控件或执行其他初始化）。|在代码之前调用基类实现，以便基类有机会创建对话框窗口和所有控件，然后再尝试更新它们。|  
    |[应用](../Topic/IPropertyPageImpl::Apply.md)|验证特性设置并更新对象。|因为它不执行任何操作除了跟踪外部调用，不需要调用基类实现。|  
    |[停用](../Topic/IPropertyPageImpl::Deactivate.md)|清理与窗口相关的项。|基类实现销毁表示属性页的对话框。  如果需要清理，在销毁之前对话框，应该在调用基类之前添加代码。|  
  
 有关示例属性页实现，请参见 [示例:实现属性页](../atl/example-implementing-a-property-page.md)。  
  
> [!NOTE]
>  如果您想在属性页的ActiveX控件，则需要更改您的向导生成的选件类派生的。  在基类列表中的 **CAxDialogImpl\<CYourClass\>** 替换 **CDialogImpl\<CYourClass\>**。  
  
## 请参阅  
 [属性页](../atl/atl-com-property-pages.md)   
 [ATLPages示例](../top/visual-cpp-samples.md)