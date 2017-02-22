---
title: "MFC ActiveX 控件向导的控件名称 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.ctl.names"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控件向导，控件名称"
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# MFC ActiveX 控件向导的控件名称
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定控件类和属性页类的名称、类型名称和控件的类型标识符。  除“简称”外，所有其他字段都可单独进行编辑。  如果更改“简称”的文本，该更改会反映在此页的所有其他字段的名称中。  此命名行为旨在使所有名称在开发控件时易于识别。  
  
 **简称**  
 提供控件的缩写名称。  默认情况下，该名称基于在**新建项目**对话框中提供的项目名称。  提供的名称决定类名、类型名称和类型标识符，除非分别更改那些字段。  
  
 **控件类名**  
 默认情况下，控件类的名称基于简称，并以 `C` 为前缀，以 `Ctrl` 为后缀。  例如，如果控件的简称是 `Price`，则控件类名为 `CPriceCtrl`。  
  
 **控件 .h 文件**  
 默认情况下，头文件的名称基于简称，并以 `Ctrl` 为后缀，以 `.h` 为文件扩展名。  例如，如果控件的简称是 `Price`，则头文件名为 `PriceCtrl.h`。  该字段中的名称应该与控件类名称匹配。  
  
 **控件 .cpp 文件**  
 默认情况下，头文件的名称基于简称，并以 `Ctrl` 为后缀，以 `.cpp` 为文件扩展名。  例如，如果控件的简称是 `Price`，则头文件名为 `PriceCtrl.cpp`。  该字段中的名称应与头文件名匹配。  
  
 **控件类型名称**  
 默认情况下，控件类型的名称基于简称，后跟 `Control`。  例如，如果控件的简称是 `Price`，则控件类的类型名是 `Price Control`。  如果更改该字段中的值，确保名称中体现继承。  
  
 **控件类型 ID**  
 设置控件类的控件类型 ID。  当控件被添加到项目时，它将该字符串写入注册表。  容器应用程序使用该字符串创建控件的实例。  
  
 默认情况下，控件类型 ID 基于简称和您在**“新建项目”**对话框中指定的项目名称。  此名称应匹配类型名。  
  
 默认情况下，控件类型 ID 如下显示：  
  
 *ProjectName*.*ShortName*Ctrl.1  
  
 如果更改此对话框中的简称，控件类型 ID 如下显示：  
  
 *ProjectName*.*NewShortName*Ctrl.1  
  
 **属性页类名**  
 默认情况下，属性页类的名称基于简称，并以 `C` 为前缀，以 `PropPage` 为后缀。  例如，如果控件的简称是 `Price`，则属性页类的名称为 `CPricePropPage`。  该名称应该与控件类的名称匹配并追加 `PropPage`。  
  
 **属性页 .h 文件**  
 默认情况下，属性页实现文件的名称基于简称，并以 `PropPage` 为后缀，以 `.h` 为文件扩展名。  例如，如果控件的简称是 `Price`，则属性页头文件名为 `PricePropPage.h`。  此名称应该与类名匹配。  
  
 **属性页 .cpp 文件**  
 默认情况下，属性页头文件的名称基于简称，并以 `PropPage` 为后缀，以 `.cpp` 为文件扩展名。  例如，如果控件的简称是 `Price`，则属性页头文件名为 `PricePropPage.cpp`。  此名称应该与头文件名匹配。  
  
 **属性页类型名称**  
 默认情况下，属性页类型名称基于简称，后跟 `Property Page`。  例如，如果控件的简称是 `Price`，则属性页类型名称为 `Price Property Page`。  如果更改该字段中的值，确保名称中体现控件类。  
  
 **属性页类型 ID**  
 设置属性页类的 ID。  当控件应用到项目时，它将该字符串写入注册表。  容器应用程序使用该字符段创建控件属性页的实例。  
  
 默认情况下，属性页类型 ID 基于简称和您在**“新建项目”**对话框中指定的项目名称。  此名称应匹配类型名。  
  
 默认情况下，属性页类型 ID 如下显示：  
  
 *ProjectName*.*ShortName*PropPage.1  
  
 如果在此对话框中更改简称，则属性页类型 ID 如下显示：  
  
 *ProjectName*.*NewShortName*PropPage.1  
  
## 请参阅  
 [MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)   
 [应用程序设置, MFC ActiveX 控件向导](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控件向导控件设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [为 Visual C\+\+ 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)