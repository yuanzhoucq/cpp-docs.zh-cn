---
title: 应用程序设置，MFC ActiveX 控件向导 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ad19a4c9726378a54bd68173decd2469c17ec75
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708561"
---
# <a name="application-settings-mfc-activex-control-wizard"></a>应用程序设置, MFC ActiveX 控件向导
使用此 MFC ActiveX 控件向导的页面来设计基本功能并将其添加到新的 MFC ActiveX 项目。 这些设置适用于应用程序本身，而非任何特定功能或控件元素。  
  
- **运行时许可证**

   选择此功能来生成用户许可证文件以与控件一起分发。 该许可证时文本文件， *projname*.lic。 文件必须位于和控件的 DLL 相同的路径中，从而使控件的实例能够在设计时环境中创建。 你通常将此文件和控件一起分发，但你的用户不会分发它。  
  
- **生成帮助文件**

   选择此选项来生成存根的帮助文件，并配置该项目为控件包含帮助。 如果不使用此选项创建的默认项目仅生成**有关**框中，当用户右键单击该控件，显示使用 f1 键或单击**帮助**上控件的容器。  
  
   > [!NOTE]
   > 帮助的显示方式取决于控件与其容器交互的方式。 如果将帮助包含在容器中，则必须处理控件和容器间的消息以适当地显示帮助。  
  
   当使用向导生成帮助文件时，项目包括以下内容：  
  
   - 文件 .vcxproj 包含代码以在创建项目时配置帮助文件。  
  
   - 该文件*projnamePropPage*.cpp 包含[SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo)构造函数中的函数。  
  
   - 文件 projname.hpj 是帮助编译器使用的帮助项目文件，创建 ActiveX 控件的帮助文件。 .hpj 文件是包含有关生成帮助文件和帮助文件所含其他文件（如位图）路径信息的文本文件。  
  
   - 该项目包括 HLP 目录以包含项目帮助位图文件和帮助主题文件 (*projname*.rtf)。 本主题包括很多 ActiveX 控件支持的常见属性、事件和方法的标准帮助主题。 可编辑 .rtf 文件以添加或删除特定帮助主题。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC ActiveX 控件向导的控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控件向导控件设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)

