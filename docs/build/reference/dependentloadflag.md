---
title: / DEPENDENTLOADFLAG （设置默认依赖加载标志）
description: /DEPENDENTLOADFLAG 选项设置为使用 LoadLibrary 加载的 Dll 的默认值标志
ms.custom: ''
ms.date: 05/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dependentloadflag
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a171f3c2edbbbf614a986ff78dd2405e734a1d1
ms.sourcegitcommit: d1f576a0f59678edc3d93508cf46485138332178
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753704"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG （设置默认依赖加载标志）

设置默认负载标志时使用`LoadLibrary`用于加载 Dll。

## <a name="syntax"></a>语法

> **/ DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>自变量

|||
|-|-|
*loadflags*|一个可选的"C"样式 16 位整数值在十进制、 八进制带前导零，或使用一个前导十六进制`0x`，，指定要应用于所有的从属负载标志[LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)调用。 默认值为 0。

## <a name="remarks"></a>备注

此选项在 Visual Studio 2017，新，并且仅适用于 Windows 10 RS1 和更高版本上运行的应用。 通过运行应用程序其他操作系统，则忽略此选项。

上支持的操作系统，此选项已更改为调用的效果`LoadLibrary("dependent.dll")`为等于`LoadLibraryEx("dependent.dll", 0, loadflags)`。 调用[LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091)不会受到影响。 此选项不适用于你的应用加载的 Dll 以递归方式。

可以使用此标志，以防止植入攻击的 DLL。 例如，如果应用使用`LoadLibrary`若要加载相关的 DLL，攻击者无法植入具有相同名称的 DLL 中使用的搜索路径`LoadLibrary`，如当前目录中，这可能之前检查系统目录是否安全 DLL 搜索模式禁用。 安全 DLL 搜索模式更高版本中的搜索顺序，使用户的当前目录，并在 Windows XP SP2 和更高版本上默认启用。 有关详细信息，请参阅[动态链接库搜索顺序](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)。

如果你指定链接选项`/DEPENDENTLOADFLAG:0xA00`(组合标志的值`LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`)，则即使用户的计算机上禁用了安全 DLL 搜索模式下，DLL 搜索路径限制为攻击者更难的受保护目录更改。 有关可用标志和其符号和数字的值，请参阅*dwFlags*参数说明中的[LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091)。

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 DEPENDENTLOADFLAG 链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入中的选项**其他选项**。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

- [设置链接器选项](setting-linker-options.md)
- [链接器选项](linker-options.md)
- [如何将隐式链接到 DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [确定要使用的链接方法](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)
- [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091)
- [动态链接库搜索顺序](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)
