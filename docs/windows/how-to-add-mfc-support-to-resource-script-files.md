---
title: 如何： 向资源脚本文件添加 MFC 支持 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.add.MFC
dev_langs:
- C++
helpviewer_keywords:
- rc files, adding MFC support
- .rc files, adding MFC support
- MFC, adding support to resource scripts files
- resource script files, adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 659c974fccec0e54dc42d6d1a5bdb019747f81ff
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647019"
---
# <a name="how-to-add-mfc-support-to-resource-script-files"></a>如何：向资源脚本文件添加 MFC 支持
通常情况下，生成用于 Windows 使用的 MFC 应用程序[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)，向导将生成一组基本的文件 （包括资源脚本 (.rc) 文件），其中包含 Microsoft 基础的核心功能类 (MFC)。 但是，如果在为不基于 MFC 的 Windows 应用程序编辑 .rc 文件，则无法使用以下特定于 MFC 框架的功能：  
  
-   MFC 代码向导 (以前称为"[MFC ClassWizard](http://msdn.microsoft.com/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)")  
  
-   菜单提示字符串  
  
-   组合框控件的列表内容  
  
-   ActiveX 控件承载  
  
 但是，可以向没有 MFC 支持的现有 .rc 文件添加这种支持。  
  
### <a name="to-add-mfc-support-to-rc-files"></a>向 .rc 文件添加 MFC 支持  
  
1.  打开资源脚本文件。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在中[资源视图](../windows/resource-view-window.md)，突出显示资源文件夹 (例如，MFC.rc)。  
  
3.  在中[属性窗口](/visualstudio/ide/reference/properties-window)，请设置**MFC Mode**属性设置为**True**。  
  
    > [!NOTE]
    >  除了设置此标志之后，.rc 文件还必须是 MFC 项目的一部分。 例如，只需设置**MFC Mode**到**True**在 Win32 中的.rc 文件上项目不会为你提供任何 MFC 功能。  
  
## <a name="requirements"></a>要求  
 MFC  
  
## <a name="see-also"></a>请参阅  
 [资源文件](../windows/resource-files-visual-studio.md)   
 [资源编辑器](../windows/resource-editors.md)