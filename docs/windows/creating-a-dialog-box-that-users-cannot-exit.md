---
title: 创建用户无法退出的对话框 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, creating
- modal dialog boxes, logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b176fbc4e420c08a2262b532cf1310ada56c978a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644175"
---
# <a name="creating-a-dialog-box-that-users-cannot-exit"></a>创建用户无法退出的对话框
可以创建用户无法退出的运行时对话框。 这种类型的对话框对于登录、应用程序或文档锁定非常有用。  
  
### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>创建用户无法退出的对话框  
  
1.  在对话框的“属性”  窗格中，将“系统菜单”  属性设置为“false” 。  
  
     这样会禁用对话框系统菜单和“关闭”  按钮。  
  
2.  在对话框窗体中，删除“取消”  和“确定”  按钮。  
  
     在运行时，用户无法退出具有以下特征的模式对话框。  
  
 若要启用这种类型的对话框中的测试，测试对话框函数检测何时**Esc**按下。 (**Esc**是也称为 VK_ESCAPE 虚拟键。)不论如何设计为对话框的以在运行时，你可以终止它在测试模式下通过按**Esc**。  
  
> [!NOTE]
>  对于 MFC 应用程序，创建一个对话框，用户无法退出，你必须重写的默认行为`OnOK`并`OnCancel`因为即使删除关联的按钮，则仍可对话框的取消按**输入**或**Esc**。  
  
 有关如何将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [如何： 创建资源](../windows/how-to-create-a-resource.md)   
 [资源文件](../windows/resource-files-visual-studio.md)   
 [对话框编辑器](../windows/dialog-editor.md)