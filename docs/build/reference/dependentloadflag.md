---
title: /DEPENDENTLOADFLAG（设置默认的依赖项加载标志）
description: /DEPENDENTLOADFLAG 选项设置使用 LoadLibrary 加载的 Dll 的默认标志
ms.date: 12/22/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 3a403f22c88ccd3e25ba95c183656ad2ffafd05a
ms.sourcegitcommit: ef34a11cb04511221bf5c7b9f4f55ad91a7a603f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/23/2019
ms.locfileid: "75329993"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG（设置默认的依赖项加载标志）

设置 `LoadLibrary` 用于加载 Dll 时使用的默认加载标志。

## <a name="syntax"></a>语法

> **/DEPENDENTLOADFLAG**[ __：__ *load_flags*]

### <a name="arguments"></a>参数

*load_flags*<br/>
一个可选的 "C" 样式16位整数值（十进制）、带前导零的八进制或带前导 `0x`的十六进制，用于指定要应用于所有[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)调用的依赖加载标志。 默认值为 0。

## <a name="remarks"></a>备注

此选项在 Visual Studio 2017 中是新增选项。 它仅适用于在 Windows 10 RS1 和更高版本上运行的应用。 运行该应用程序的其他操作系统将忽略此选项。

在支持的操作系统上，此选项的效果是将对的调用更改为与 `LoadLibraryEx("dependent.dll", 0, load_flags)`等效的 `LoadLibrary("dependent.dll")`。 对[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)的调用不受影响。 此选项不会以递归方式应用于应用加载的 Dll。

此标志可用于使[DLL 种植攻击](/windows/win32/dlls/dynamic-link-library-security)更难。 例如，如果应用程序使用 `LoadLibrary` 加载依赖 DLL，则攻击者可能会在 `LoadLibrary`所使用的搜索路径中植物同名的 DLL，例如当前目录，如果禁用了安全 DLL 搜索模式，则可能会在系统目录之前进行检查。 安全 DLL 搜索模式将在以后的搜索顺序中放置用户的当前目录，并且默认情况下在 Windows XP SP2 和更高版本上启用。 有关详细信息，请参阅[动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)。

如果指定链接选项 `/DEPENDENTLOADFLAG:0xA00` （组合标志的值 `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`），则即使在用户的计算机上禁用了安全 DLL 搜索模式，DLL 搜索路径也仅限于应用程序目录，然后是%windows%\system32 目录。 `/DEPENDENTLOADFLAG:0x800` 选项更为严格，因此限制搜索%windows%\system32 目录。 受保护的目录更难，但对于攻击者而言，这是不可能的。 有关可用标志及其符号和数值的信息，请参阅[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)中的*dwFlags*参数说明。 有关使用各种依赖加载标志时使用的搜索顺序的信息，请参阅[使用 LOAD_LIBRARY_SEARCH 标志搜索顺序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags)。

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置 DEPENDENTLOADFLAG 链接器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “链接器” > “命令行”属性页。

1. 在 "**其他选项**" 中输入选项。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>另请参阅

- [MSVC 链接器参考](linking.md)
- [MSVC 链接器选项](linker-options.md)
- [将可执行文件链接到 DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [将可执行文件链接到 DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [动态链接库搜索顺序](/windows/win32/Dlls/dynamic-link-library-search-order)
