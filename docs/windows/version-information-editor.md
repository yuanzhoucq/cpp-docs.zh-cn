---
title: 版本信息编辑器 （c + +）
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
ms.openlocfilehash: 8382371acfd423f8c6864e816b0357e3ef11718e
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210973"
---
# <a name="version-information-editor-c"></a>版本信息编辑器 （c + +）

版本信息包括公司和产品标识、产品发行版号以及版权与商标通知。 与**版本信息编辑器**，创建和维护此存储在版本信息资源中的数据。 版本信息资源不必需的应用程序，但它是一个很好的收集标识的应用程序的信息。 安装 API 也使用版本信息。

> [!NOTE]
> Windows 标准是只具有一个名为 VS_VERSION_INFO 的版本资源。

版本信息资源有一个上部块和一个或多个下部块：顶部有一个固定信息块，底部有一个或多个版本信息块（适用于其他语言和/或字符集）。 顶部块设有可编辑的数字框和可选择的下拉列表。 下部块仅包含可编辑的文本框。

> [!NOTE]
> 使用时**版本信息编辑器**，在许多情况下你可以右击以显示特定于资源的命令的快捷菜单。 例如，如果选择在指向块头条目时，快捷菜单会显示**新建版本块信息**并**删除版本块信息**命令。

## <a name="how-to"></a>操作说明

**版本信息编辑器**，可以：

### <a name="to-edit-a-string-in-a-version-information-resource"></a>编辑版本信息资源中的字符串

选择相应项目一次，然后再次选择它，以开始编辑它。 进行更改直接在**版本信息**表中或在[属性窗口](/visualstudio/ide/reference/properties-window)。 进行的更改会在这两个位置得到反映。

编辑时`FILEFLAGS`中的键**版本信息编辑器**，请注意，不能设置**调试**， **Private Build**，或**Special Build**中的属性**属性**.rc 文件的窗口：

   - **版本信息编辑器**设置**调试**具有属性`#ifdef`在资源脚本中，基于`_DEBUG`生成标志。

  - 如果`Private Build`密钥都有**值**中设置**版本信息**表中，相应**Private Build**属性中的**属性**窗口`FILEFLAGS`键将为**True**。 如果**值**是空的则该属性为**False**。 同样， **Special Build**中的键**版本信息**表绑定到**Special Build**属性`FILEFLAGS`密钥。

可以通过选择字符串块的信息序列进行排序**键**或**值**列标题。 这些标题会自动将信息重新排列为所选顺序。

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>若要添加另一种语言 （新版本信息块） 的版本信息

1. 通过在 [资源视图](../windows/resource-view-window.md)中双击鼠标打开版本信息资源。

1. 在版本信息表中右键单击并选择**新版本信息块**。

   此命令将其他信息块添加到当前版本信息资源，并在 [属性窗口](/visualstudio/ide/reference/properties-window)中打开其相应属性。

1. 在“属性”  窗口中，为新块选择合适的语言和字符集。

### <a name="to-delete-a-version-information-block"></a>删除版本信息块

1. 通过在 [资源视图](../windows/resource-view-window.md)中双击图标来打开版本信息资源。

1. 右键单击想要删除选择的块标头**删除版本信息块**。

   此命令将删除所选标头，并使版本信息的其余部分保持不变。 不能撤消操作。

### <a name="to-access-version-information-from-within-your-program"></a>在程序内访问版本信息

如果想要在程序内访问版本信息，请使用 [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) 函数和 [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) 函数。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源编辑器](../windows/resource-editors.md)<br/>
<!--
[Menus and Other Resources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Version Information (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)-->
