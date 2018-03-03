---
title: "Win32 预定义符号 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols, Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 865d61611546e2550aaa241220dc226cea9f9b81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="win32-predefined-symbols"></a>Win32 预定义符号
在 Win32 标头文件中，定义了这些符号和它们支持标准 Windows 应用程序功能和操作。 这些符号主要用于公共用户界面元素。 当你正在使用资源编辑器中的控件时，这些符号将出现在[属性窗口](/visualstudio/ide/reference/properties-window)与公共控件关联。 例如，如果您的工具栏上应显示应用程序图标，该图标可以为与属性窗口中的符号 IDI_SMALL 相关联。  
  
|||  
|-|-|  
|IDABORT|控制: 对话框的中止按钮|  
|IDC_STATIC|在对话框中的控件： 静态文本|  
|IDCANCEL|控制: 对话框的取消按钮|  
|IDD_ABOUTBOX|有关对话框中的对话框： 产品|  
|IDI_PROJECTNAME|图标: 当前项目图标|  
|IDI_SMALL|图标： 当前项目小图标|  
|IDIGNORE|用于对话框上的忽略按钮的控件：|  
|IDM_ABOUT|菜单项： 用于帮助...有关...|  
|IDM_EXIT|与文件一起使用菜单项:...退出...|  
|IDNO|控制： 对话框中没有按钮|  
|IDOK|控件： 对话框确定按钮|  
|IDRETRY|控制: 对话框的重试按钮|  
|IDS_APP_TITLE|字符串： 当前应用程序名称|  
|IDYES|控制： 对话框中是按钮|  
  
## <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [预定义的符号 Id](../windows/predefined-symbol-ids.md)   
 [符号：资源标识符](../windows/symbols-resource-identifiers.md)