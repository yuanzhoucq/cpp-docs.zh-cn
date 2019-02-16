---
title: ATL 预定义的符号
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
ms.openlocfilehash: bb8b0db77b2add584e2fa8716a2d1821f5cae1fc
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320453"
---
# <a name="atl-predefined-symbols"></a>ATL 预定义的符号

在 ATL 标头文件中，定义了这些符号，但它们支持标准的 Windows 应用程序功能和操作。 这些符号主要用于对话框。 当您正在使用对话框和控件中[对话框编辑器](../windows/dialog-editor.md)，这些符号将出现在**属性**与公共控件关联的窗口。 例如，如果您的对话框具有**取消**按钮，命令将与相关联的符号 IDCANCEL 中[属性窗口](/visualstudio/ide/reference/properties-window)。

|||
|-|-|
|IDABORT|控制：对话框中止按钮|
|IDC_STATIC|控制：静态控件|
|IDCANCEL|控制：对话框取消按钮|
|IDIGNORE|控制：对话框忽略按钮|
|IDNO|控制：对话框的按钮|
|IDOK|控制：对话框确定按钮|
|IDR_ACCELERATOR1|资源：快捷键对应表|
|IDRETRY|控制：对话框重试按钮|
|IDS_PROJNAME|字符串：当前应用程序名称|
|IDYES|控制：对话框是按钮|

## <a name="requirements"></a>要求

ATL

## <a name="see-also"></a>请参阅

[预定义的符号 ID](../windows/predefined-symbol-ids.md)<br/>
[MFC 预定义的符号](../windows/mfc-predefined-symbols.md)<br/>
[Win32 预定义符号](../windows/win32-predefined-symbols.md)<br/>