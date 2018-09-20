---
title: Win32 预定义的符号 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols [C++], Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18edb56c03541f61607817d14fdbadb067a3630d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422774"
---
# <a name="win32-predefined-symbols"></a>Win32 预定义符号

Win32 头文件中定义了这些符号，并且它们支持标准的 Windows 应用程序功能和操作。 这些符号主要用于公共用户界面元素。 当您正在使用资源编辑器中的控件时，这些符号将出现在[属性窗口](/visualstudio/ide/reference/properties-window)与公共控件相关联。 例如，如果您的工具栏应显示应用程序图标，图标将与关联的符号 IDI_SMALL 中**属性窗口**。

|||
|-|-|
|IDABORT|控件: 对话框的中止按钮|
|IDC_STATIC|在对话框中的控件： 静态文本|
|IDCANCEL|控件: 对话框的取消按钮|
|IDD_ABOUTBOX|关于对话框的对话框： 产品|
|IDI_PROJECTNAME|图标: 当前项目图标|
|IDI_SMALL|图标： 当前项目小图标|
|IDIGNORE|使用忽略按钮的对话框上使用控件：|
|IDM_ABOUT|菜单项： 用于帮助...有关...|
|IDM_EXIT|与文件一起使用的菜单项:...退出...|
|IDNO|控制： 对话框中的按钮|
|IDOK|控件： 对话框确定按钮|
|IDRETRY|控件: 对话框的重试按钮|
|IDS_APP_TITLE|字符串： 当前应用程序名称|
|IDYES|是按钮控件: 对话框|

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[预定义的符号 ID](../windows/predefined-symbol-ids.md)<br/>
[符号：资源标识符](../windows/symbols-resource-identifiers.md)