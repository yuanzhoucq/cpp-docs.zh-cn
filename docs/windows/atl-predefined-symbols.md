---
title: ATL 预定义的符号 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c00487b2bb7c7a67dfb81ffb638f5a46fc611bc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="atl-predefined-symbols"></a>ATL 预定义的符号
在 ATL 标头文件中，定义了这些符号，但它们支持标准 Windows 应用程序功能和操作。 这些符号主要用于显示对话框。 当你正在使用对话框和控件中[对话框编辑器](../windows/dialog-editor.md)，这些符号将出现在属性窗口中与公共控件关联。 例如，如果对话框中具有取消按钮，该命令将与关联的符号 IDCANCEL 中[属性窗口](/visualstudio/ide/reference/properties-window)。  
  
|||  
|-|-|  
|IDABORT|控制: 对话框的中止按钮|  
|IDC_STATIC|控件： 静态控件|  
|IDCANCEL|控制: 对话框的取消按钮|  
|IDIGNORE|控制: 对话框的忽略按钮|  
|IDNO|控制： 对话框中没有按钮|  
|IDOK|控件： 对话框确定按钮|  
|IDR_ACCELERATOR1|资源： 快捷键对应表|  
|IDRETRY|控制: 对话框的重试按钮|  
|IDS_PROJNAME|字符串： 当前应用程序名称|  
|IDYES|控制： 对话框中是按钮|  
  
## <a name="requirements"></a>要求  
 ATL  
  
## <a name="see-also"></a>请参阅  
 [预定义的符号 Id](../windows/predefined-symbol-ids.md)   
 [符号：资源标识符](../windows/symbols-resource-identifiers.md)