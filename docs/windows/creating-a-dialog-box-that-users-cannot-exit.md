---
title: "创建用户无法退出的对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes, creating
- modal dialog boxes, logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1b53c233c13ed53f4cf2ccf489da9af90ae15796
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-dialog-box-that-users-cannot-exit"></a>创建用户无法退出的对话框
可以创建用户无法退出的运行时对话框。 这种类型的对话框对于登录、应用程序或文档锁定非常有用。  
  
### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>创建用户无法退出的对话框  
  
1.  在对话框的“属性”  窗格中，将“系统菜单”  属性设置为“false” 。  
  
     这样会禁用对话框系统菜单和“关闭”  按钮。  
  
2.  在对话框窗体中，删除“取消”  和“确定”  按钮。  
  
     在运行时，用户无法退出具有以下特征的模式对话框。  
  
 要对这种对话框进行测试，测试对话框函数可以在按下 Esc 键时检测。 （ESC 是也称为 VK_ESCAPE 虚拟键。）不论如何设计运行时的对话框行为，都可以通过在测试模式下按 Esc 键终止。  
  
> [!NOTE]
>  对于 MFC 应用程序，要创建一个用户无法退出的对话框，必须重写 `OnOK` 和“确定” `OnCancel` 的默认行为，因为即使删除关联按钮，仍可通过按 ENTER 或 ESC 键来取消对话框。  
  
 有关如何将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)。  
  
## <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [如何： 创建资源](../windows/how-to-create-a-resource.md)   
 [资源文件](../windows/resource-files-visual-studio.md)   
 [对话框编辑器](../windows/dialog-editor.md)

