---
title: /DEPENDENTLOADFLAG（设置默认的依赖项加载标志）
description: /DEPENDENTLOADFLAG 选项设置使用 LoadLibrary 加载的 Dll 的默认标志
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 072fa1103d049c7d5c395ae88d268f3b47e20b4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492956"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG（设置默认的依赖项加载标志）

设置用于加载 dll 时`LoadLibrary`使用的默认加载标志。

## <a name="syntax"></a>语法

> **/DEPENDENTLOADFLAG**[ **:** _loadflags_]

### <a name="arguments"></a>自变量

*loadflags*<br/>
一个可选的 "C" 样式16位整数值 (十进制)、带有前导零的八进制或带前导`0x`零的十六进制 (指定要应用于所有[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)调用的依赖加载标志)。 默认值为 0。

## <a name="remarks"></a>备注

此选项在 Visual Studio 2017 中是新增选项, 并且仅适用于在 Windows 10 RS1 及更高版本上运行的应用。 运行该应用程序的其他操作系统将忽略此选项。

在支持的操作系统上, 此选项可将对的调用`LoadLibrary("dependent.dll")`更改为等效的。 `LoadLibraryEx("dependent.dll", 0, loadflags)` 对[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)的调用不受影响。 此选项不会以递归方式应用于应用加载的 Dll。

此标志可用于防止 DLL 种植攻击。 例如, 如果应用程序使用`LoadLibrary`加载依赖 DLL, 则攻击者可能会在所`LoadLibrary`使用的搜索路径中植物同名的 dll, 例如当前目录, 在安全 DLL 搜索模式为的情况下, 可能会在系统目录之前进行检查disabled. 安全 DLL 搜索模式将在以后的搜索顺序中放置用户的当前目录, 并且默认情况下在 Windows XP SP2 和更高版本上启用。 有关详细信息, 请参阅[动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)。

如果指定链接选项`/DEPENDENTLOADFLAG:0xA00` (组合标志`LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`的值), 则即使在用户的计算机上禁用了安全 DLL 搜索模式, DLL 搜索路径也仅限于受保护的目录, 攻击者更难转. 有关可用标志及其符号和数值的信息, 请参阅[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)中的*dwFlags*参数说明。

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 DEPENDENTLOADFLAG 链接器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > **链接器** > **命令行**" 属性页。

1. 在 "**其他选项**" 中输入选项。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

- [MSVC 链接器参考](linking.md)
- [MSVC 链接器选项](linker-options.md)
- [将可执行文件链接到 DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [将可执行文件链接到 DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)
