---
title: /DEPENDENTLOADFLAG（设置默认的依赖项加载标志）
description: /DEPENDENTLOADFLAG 选项为此模块加载的 Dll 设置默认的依赖加载标志。
ms.date: 01/22/2020
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 5e31a0d747e7186814cba3ae1c4cf243569d87a8
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725703"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG（设置默认的依赖项加载标志）

::: moniker range="vs-2015"

**/DEPENDENTLOADFLAG**选项需要 Visual Studio 2017 或更高版本。

::: moniker-end

::: moniker range=">=vs-2017"

设置在操作系统解析模块的静态链接导入时使用的默认加载标志。

## <a name="syntax"></a>语法

> **/DEPENDENTLOADFLAG**[ __：__ *load_flags*]

### <a name="arguments"></a>参数

*load_flags*<br/>
一个可选的整数值，指定在解析模块的静态链接的导入依赖项时要应用的加载标志。 默认值为 0。 有关支持的标志值的列表，请参阅[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)中的 `LOAD_LIBRARY_SEARCH_*` 条目。

## <a name="remarks"></a>备注

当操作系统解析模块的静态链接的导入时，它将使用[默认的搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order)。 使用 **/DEPENDENTLOADFLAG**选项指定更改用于解决这些导入的搜索路径的*load_flags*值。 在支持的操作系统上，它会更改静态导入分辨率搜索顺序，与使用 `LOAD_LIBRARY_SEARCH` 参数时[的情况类似](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)。 有关*load_flags*所设置的搜索顺序的信息，请参阅[使用 LOAD_LIBRARY_SEARCH 标志的搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags)。

此标志可用于使一个[DLL 种植攻击](/windows/win32/dlls/dynamic-link-library-security)向量更难。 例如，假设某个应用具有静态链接的 DLL：

- 攻击者可能会在导入分辨率搜索路径（如应用程序目录）之前，植物同名的 DLL。 受保护的目录更难，但对于攻击者而言，这是不可能的。

- 如果应用程序、%windows%\system32 和% windows% 目录中缺少 DLL，则导入解析将贯穿到当前目录。 攻击者可能会在那里植物一个 DLL。

在这两种情况下，如果 `/DEPENDENTLOADFLAG:0x800` 指定了 link 选项（标志 `LOAD_LIBRARY_SEARCH_SYSTEM32`的值），则模块搜索路径将限制为%windows%\system32 目录。 它为其他目录的种植攻击提供了一些保护。 有关详细信息，请参阅[动态链接库安全性](/windows/win32/dlls/dynamic-link-library-security)。

若要查看任何 DLL 中由 **/DEPENDENTLOADFLAG**选项设置的值，请使用带有[/LOADCONFIG](loadconfig.md)选项的[DUMPBIN](dumpbin-reference.md)命令。

**/DEPENDENTLOADFLAG**选项是 Visual Studio 2017 中的新增选项。 它仅适用于在 Windows 10 RS1 和更高版本上运行的应用。 运行该应用程序的其他操作系统将忽略此选项。

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 DEPENDENTLOADFLAG 链接器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. >**链接器**> "**命令行**" 属性页中选择**配置属性**。

1. 在 "**其他选项**" 中输入选项。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>另请参阅

- [MSVC 链接器参考](linking.md)
- [MSVC 链接器选项](linker-options.md)
- [隐式将可执行文件链接到 DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [确定要使用的链接方法](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)
- [动态链接库安全性](/windows/win32/dlls/dynamic-link-library-security)

::: moniker-end
