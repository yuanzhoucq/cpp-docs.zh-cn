---
title: "控件名称，MFC ActiveX 控件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.ctl.names
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f3444ec69ea96ee89ed7a0965f3575fc79e3b9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="control-names-mfc-activex-control-wizard"></a>MFC ActiveX 控件向导的控件名称
指定控件类和属性页类，类型名称的名称和类型为您的控件的标识符。 除**短名称**，所有其他字段可单独进行编辑。 如果你更改的文本**短名称**，在此页中的所有其他字段的名称中会反映更改。 此命名行为旨在使所有名称轻松地识别为您开发您的控件。  
  
 **短名称**  
 提供控件的缩写的名称。 默认情况下，此名称基于中提供的项目名称**新项目**对话框。 您提供的名称确定类名称、 类型名称和类型标识符，除非您单独更改这些字段。  
  
 **控件类名**  
 默认情况下，控件类的名称基于的短名称，并与`C`作为前缀和`Ctrl`作为后缀。 例如，如果你的控件的短名称，则`Price`，控件类名称是`CPriceCtrl`。  
  
 **控制.h 文件**  
 默认情况下，标头文件的名称基于的短名称，并与`Ctrl`作为后缀和`.h`作为文件扩展名。 例如，如果你的控件的短名称，则`Price`，头文件的名称是`PriceCtrl.h`。 此字段中的名称应与控件类名称匹配。  
  
 **控制.cpp 文件**  
 默认情况下，标头文件的名称基于的短名称，并与`Ctrl`作为后缀和`.cpp`作为文件扩展名。 例如，如果你的控件的短名称，则`Price`，头文件的名称是`PriceCtrl.cpp`。 此字段中的名称应与标头名称匹配。  
  
 **控件类型名称**  
 默认情况下，控件类型的名称基于短名称后, 跟`Control`。 例如，如果你的控件的短名称，则`Price`，控件类类型名称是`Price Control`。 如果更改此字段中的值，请确保该名称指示继承。  
  
 **控件类型 ID**  
 设置的控件类的控件类型 ID。 添加到项目时，控件将该字符串写入到注册表中。 容器应用程序使用此字符串创建的控件实例。  
  
 默认情况下，控件类型 ID 基于项目名称，在中指示**新项目**对话框中，和短名称。 此名称应与匹配的类型名称。  
  
 默认情况下，控件类型 ID 如下所示：  
  
 *形式*ctrl.1;  
  
 如果更改此对话框中的短名称，控件类型 ID 如下所示：  
  
 *项目*ctrl.1;  
  
 **属性页类名**  
 默认情况下，属性页类的名称基于的短名称，并与`C`作为前缀和`PropPage`作为后缀。 例如，如果你的控件的短名称，则`Price`，属性页类名称是`CPricePropPage`。 此名称应与匹配在控件类名称后追加`PropPage`。  
  
 **属性页.h 文件**  
 默认情况下，属性页标头文件的名称基于的短名称，并以`PropPage`作为后缀和`.h`作为文件扩展名。 例如，如果你的控件的短名称，则`Price`，属性页头文件的名称是`PricePropPage.h`。 此名称应与类名称匹配。  
  
 **属性页.cpp 文件**  
 默认情况下，属性页实现文件的名称基于的短名称，并以`PropPage`作为后缀和`.cpp`作为文件扩展名。 例如，如果你的控件的短名称，则`Price`，属性页头文件的名称是`PricePropPage.cpp`。 此名称应与头文件的名称匹配。  
  
 **属性页类型名称**  
 默认情况下，属性页类型名称基于短名称后, 跟`Property Page`。 例如，如果你的控件的短名称，则`Price`，属性页类型名称是`Price Property Page`。 如果更改此字段中的值，请确保该名称指示的控件类。  
  
 **属性页类型 ID**  
 设置属性页类的 ID。 应用到一个项目时，控件将该字符串写入注册表中。 容器应用程序使用此字符串来创建控件的属性页的实例。  
  
 默认情况下，属性页类型 ID 基于项目名称，在中指示**新项目**对话框中，和短名称。 此名称应与匹配的类型名称。  
  
 默认情况下，属性页类型 ID 如下所示：  
  
 *形式*PropPage.1  
  
 如果更改此对话框中的短名称，属性页类型 ID 将显示如下：  
  
 *项目*PropPage.1  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)   
 [应用程序设置，MFC ActiveX 控件向导](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控件向导控件设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [为 Visual C++ 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)

