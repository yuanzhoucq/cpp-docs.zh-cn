---
title: / DEPENDENTLOADFLAG （设置默认依赖加载标志）
description: /DEPENDENTLOADFLAG 选项用于将默认标志设置为使用 LoadLibrary 加载的 Dll
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 94998e06f23a7e70524221d3cb75166b5d3f2c44
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815965"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG （设置默认依赖加载标志）

设置默认负载标志时使用`LoadLibrary`用于加载 Dll。

## <a name="syntax"></a>语法

> **/DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>自变量

*loadflags*<br/>
一个可选的"C"样式 16 位整数值在十进制、 八进制带前导零，或带有前导十六进制`0x`，指定要应用于所有的依赖加载标志[LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)调用。 默认值为 0。

## <a name="remarks"></a>备注

此选项在 Visual Studio 2017 中，新，仅适用于 Windows 10 RS1 和更高版本上运行的应用。 通过运行应用其他操作系统，则忽略此选项。

上支持的操作系统，此选项已更改为调用的效果`LoadLibrary("dependent.dll")`为等于`LoadLibraryEx("dependent.dll", 0, loadflags)`。 调用[LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)不会受到影响。 此选项不适用于您的应用程序所加载的 Dll 以递归方式。

可以使用此标志，以防止 DLL 植入攻击。 例如，如果一个应用程序使用`LoadLibrary`若要加载的依赖 DLL，攻击者无法计划具有相同名称的 DLL 中使用的搜索路径`LoadLibrary`，如当前目录中，这可能前检查系统目录是否安全 DLL 搜索模式已禁用。 安全 DLL 搜索模式更高版本中的搜索顺序，将用户的当前目录，并在 Windows XP SP2 和更高版本上的默认情况下启用。 有关详细信息，请参阅[动态链接库搜索顺序](/windows/desktop/Dlls/dynamic-link-library-search-order)。

如果指定了链接选项`/DEPENDENTLOADFLAG:0xA00`(组合的标志的值`LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`)，则即使在用户计算机上禁用安全 DLL 搜索模式，则 DLL 搜索路径是限制为受保护到攻击者更难的目录，更改。 了解可用的标志和其符号和数字值，请参阅*dwFlags*中的参数说明[LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)。

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 DEPENDENTLOADFLAG 链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入中的选项**其他选项**。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

- [MSVC 链接器引用](linking.md)
- [MSVC 链接器选项](linker-options.md)
- [将可执行文件链接到 DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [将可执行文件链接到 DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)
- [动态链接库搜索顺序](/windows/desktop/Dlls/dynamic-link-library-search-order)
