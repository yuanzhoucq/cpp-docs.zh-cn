---
title: 版本信息编辑器（C++）
ms.date: 02/14/2019
f1_keywords:
- vc.editors.version.F1
- vc.editors.version
helpviewer_keywords:
- Version Information editor [C++], about Version Information editor
- editors, Version Information
- resource editors [C++], Version Information editor
- version information resources [C++]
- resources [C++], editing version information
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
ms.openlocfilehash: b083ed27b6b1f471dbec9b96e7be7a6165f8d125
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214365"
---
# <a name="version-information-editor-c"></a>版本信息编辑器（C++）

版本信息包括公司和产品标识、产品发行版号以及版权与商标通知。 利用**版本信息编辑器**，可以创建和维护存储在版本信息资源中的这些数据。 应用程序不需要版本信息资源，但它是收集标识应用程序的信息的有用位置。 安装 API 也使用版本信息。

> [!NOTE]
> Windows 标准是只具有一个名为 VS_VERSION_INFO 的版本资源。

版本信息资源有一个上部块和一个或多个下部块：顶部有一个固定信息块，底部有一个或多个版本信息块（适用于其他语言和/或字符集）。 顶部块设有可编辑的数字框和可选择的下拉列表。 下部块仅包含可编辑的文本框。

> [!NOTE]
> 使用**版本信息编辑器**时，在许多情况下，您可以右键单击以显示特定于资源的命令的快捷菜单。 例如，如果选择指向块标头条目，快捷菜单将显示 "**新建版本块信息**" 和 "**删除版本块信息**" 命令。

## <a name="how-to"></a>如何

**版本信息编辑器**使你能够：

### <a name="to-edit-a-string-in-a-version-information-resource"></a>编辑版本信息资源中的字符串

选择该项目一次进行选择，然后再次开始编辑它。 直接在**版本信息**表中或在[属性窗口](/visualstudio/ide/reference/properties-window)中进行更改。 进行的更改会在这两个位置得到反映。

在**版本信息编辑器**中编辑 `FILEFLAGS` 项时，请注意，不能在 .rc 文件的 "**属性**" 窗口中设置 "**调试**"、"**专用生成**" 或 "**特殊生成**" 属性：

- **版本信息编辑器**将根据 `_DEBUG` 生成标志，在资源脚本中使用 `#ifdef` 设置**Debug**属性。

- 如果 `Private Build` 键在**版本信息**表中设置了**值**，则 `FILEFLAGS` 项的 "**属性**" 窗口中的相应 "**私有生成**" 属性将为**True**。 如果**值**为空，则属性将为**False**。 同样，**版本信息**表中的**特殊生成**键将绑定到 `FILEFLAGS` 键的**特殊生成**属性。

您可以通过选择**键**或**值**列标题来对字符串块的信息序列进行排序。 这些标题会自动将信息重新排列为所选顺序。

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>添加其他语言的版本信息（新版本信息块）

1. 通过在 [资源视图](how-to-create-a-resource-script-file.md#create-resources)中双击鼠标打开版本信息资源。

1. 在版本信息表中右键单击，然后选择 "**新建版本信息块**"。

   此命令将其他信息块添加到当前版本信息资源，并在 [属性窗口](/visualstudio/ide/reference/properties-window)中打开其相应属性。

1. 在“属性” 窗口中，为新块选择合适的语言和字符集。

### <a name="to-delete-a-version-information-block"></a>删除版本信息块

1. 通过在 [资源视图](how-to-create-a-resource-script-file.md#create-resources)中双击图标来打开版本信息资源。

1. 右键单击要删除的块标头，然后选择 "**删除版本信息块**"。

   此命令删除所选的标头，并使其余的版本信息保持不变。 不能撤消该操作。

### <a name="to-access-version-information-from-within-your-program"></a>在程序内访问版本信息

如果想要在程序内访问版本信息，请使用 [GetFileVersionInfo](/windows/win32/api/winver/nf-winver-getfileversioninfow) 函数和 [VerQueryValue](/windows/win32/api/winver/nf-winver-verqueryvaluew) 函数。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
[菜单和其他资源](/windows/win32/menurc/resources)<br/>
[版本信息 (Windows)](/windows/win32/menurc/version-information)
