---
title: MIDL 编译器属性页
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 57498a01-fccc-4a0e-a036-6ff702f83126
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.AdditionalMetadataDirectories
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.MultiProcMIDL
- VC.Project.VCMidlTool.OutputDirectory
- VC.Project.VCMidlTool.WinmdFileName
- VC.Project.VCMidlTool.HeaderFileName
- VC.Project.VCMidlTool.DLLDataFileName
- VC.Project.VCMidlTool.InterfaceIdentifierFileName
- VC.Project.VCMidlTool.ProxyFileName
- VC.Project.VCMidlTool.GenerateTypeLibrary
- VC.Project.VCMidlTool.TypeLibraryName
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.TypeLibFormat
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.PreendWithABINamepsace
- VC.Project.VCMidlTool.ValidateParameters
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.MinimumTargetSystem
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: d6833230baca892836c187799df7f0658aa16772
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336243"
---
# <a name="midl-property-pages"></a>“MIDL”属性页

MIDL 属性页作为 项属性在 上可用。使用 COM 的C++项目中的 IDL 文件。 使用它们来配置[MIDL编译器](/windows/win32/midl/using-the-midl-compiler-2)。 有关如何以编程方式访问 C++ 项目的 MIDL 选项的信息，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> 对象。 另请参阅[常规 MIDL 命令行语法](/windows/win32/midl/general-midl-command-line-syntax)。

## <a name="general-property-page"></a>“常规属性”页

### <a name="preprocessor-definitions"></a>预处理器定义

指定一个或多个定义，包括 MIDL 宏 （[/D](/windows/win32/midl/-d)\[）\]宏 。

### <a name="additional-include-directories"></a>附加包含目录

指定要添加到包含路径[（/I](/windows/win32/midl/-i)\[路径\]） 的一个或多个目录。

### <a name="additional-metadata-directories"></a>其他元数据目录

指定包含 Windows.Foundation.WinMD 文件的目录[（/metadata_dir](/windows/win32/midl/-metadata-dir)\[路径\]）。

### <a name="enable-windows-runtime"></a>启用 Windows 运行时

启用 Windows 运行时语义以创建 Windows 元数据文件[（/winrt](/windows/win32/midl/-winrt)）。

### <a name="ignore-standard-include-path"></a>忽略标准包含路径

忽略当前目录和 INCLUDE 目录[（/no_def_idir](/windows/win32/midl/-no-def-idir)）。

### <a name="mktyplib-compatible"></a>MkTypLib 兼容

强制兼容 mktyplib.exe 版本 2.03[（/mktyplib203](/windows/win32/midl/-mktyplib203)）。

### <a name="warning-level"></a>警告级别

选择 MIDL 代码错误的严格性 （[/W](/windows/win32/midl/-w)）。

**选择**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>将警告视为错误

使 MIDL 将所有警告视为错误[（/WX](/windows/win32/midl/-wx)）。

### <a name="suppress-startup-banner"></a>取消显示启动版权标志

禁止显示启动横幅和信息消息[（/nologo）。](/windows/win32/midl/-nologo)

### <a name="c-compiler-char-type"></a>C 编译器字符类型

指定将用于编译生成的代码的 C 编译器的默认字符类型。 [（/字符](/windows/win32/midl/-char)签名_未签名_ascii7）。

**选择**

- **已签名**- 已签名
- **未签名**- 未签名
- **阿西**- 阿西

### <a name="target-environment"></a>目标环境

指定要定位的环境[（/env](/windows/win32/midl/-env)臂 32_win32_ia64_x64）。

**选择**

- **未设置**- 赢 32
- **微软视窗 32 位**- Win32
- **微软视窗 64 位上 Itanium** - IA64
- **微软视窗 ARM** - ARM
- **微软视窗ARM64** - ARM64
- **微软视窗 64 位 x64** - X64

### <a name="generate-stubless-proxies"></a>生成无存代理

生成具有对象接口[（/Oicf](/windows/win32/midl/-oi)， [/Oif）](/windows/win32/midl/-oi)的扩展和无存根代理的完全解释的存根。

### <a name="suppress-compiler-warnings"></a>取消显示编译器警告

禁止编译器警告消息[（/no_warn](/windows/win32/midl/-no-warn)）。

### <a name="application-configuration-mode"></a>应用程序配置模式

允许在 IDL 文件中选择 ACF 属性[（/app_config](/windows/win32/midl/-app-config)）。

### <a name="locale-id"></a>区域设置 ID

指定输入文件、文件名和目录路径[（/lcid](/windows/win32/midl/-lcid) DECIMAL） 的 LCID。

### <a name="multi-processor-compilation"></a>多处理器编译

同时运行多个实例。

## <a name="output-property-page"></a>输出属性页

### <a name="output-directory"></a>输出目录

指定输出目录[（/out](/windows/win32/midl/-out) [目录]）。

### <a name="metadata-file"></a>元数据文件

指定生成的元数据文件[（/winmd](/windows/win32/midl/-winmd)文件名）的名称。

### <a name="header-file"></a>标头文件

指定生成的标头文件[（/h](/windows/win32/midl/-h)文件名）的名称。

### <a name="dlldata-file"></a>DllData 文件

指定 DLLDATA 文件[（/dlldata](/windows/win32/midl/-dlldata)文件名） 的名称。

### <a name="iid-file"></a>IID 文件

指定接口标识符文件[（/iid](/windows/win32/midl/-iid)文件名） 的名称。

### <a name="proxy-file"></a>代理文件

指定代理文件[（/代理](/windows/win32/midl/-proxy)文件名）的名称。

### <a name="generate-type-library"></a>生成类型库

指定不生成类型库（\/notlb= 否）。

### <a name="type-library"></a>类型库

指定类型库文件[（/tlb](/windows/win32/midl/-tlb)文件名） 的名称。

### <a name="generate-client-stub-files"></a>生成客户端存根文件

仅生成客户端存根文件[（/客户端](/windows/win32/midl/-client)[存根]无）。

**选择**

- **存根**- 存根
- **无**- 无

### <a name="generate-server-stub-files"></a>生成服务器存根文件

仅生成服务器存根文件[（/服务器](/windows/win32/midl/-server)[存根]无）。

**选择**

- **存根**- 存根
- **无**- 无

### <a name="client-stub-file"></a>客户端存根文件

指定客户端存根文件[（/cstub](/windows/win32/midl/-cstub) [文件]）。

### <a name="server-stub-file"></a>服务器存根文件

指定服务器存根文件[（/stub](/windows/win32/midl/-sstub) [文件]）。

### <a name="type-library-format"></a>类型库格式

指定类型库文件格式（*/旧\tlb_/newtlb*）。

**选择**

- **新格式**- 新格式
- **旧格式**- 旧格式

## <a name="advanced-property-page"></a>高级属性页

### <a name="c-preprocess-options"></a>C 预处理选项

指定交换机以传递给 C 编译器预处理器[（/cpp_opt](/windows/win32/midl/-cpp-opt)交换机）。

### <a name="undefine-preprocessor-definitions"></a>取消定义预处理器定义

指定一个或多个未定义，包括 MIDL 宏[（/U](/windows/win32/midl/-U) [宏]）。

### <a name="enable-error-checking"></a>启用错误检查

选择错误检查选项（*/错误全部=无]）。

**选择**

- **启用自定义**- 全部
- **全部**- 全部
- **无**- 无

### <a name="check-allocations"></a>检查分配

检查内存不足错误[（/错误](/windows/win32/midl/-error)分配）。

### <a name="check-bounds"></a>检查边界

检查大小与传输长度规格[（/错误](/windows/win32/midl/-error)bounds_check）。

### <a name="check-enum-range"></a>检查枚举范围

检查枚举值是否在允许范围内[（/错误](/windows/win32/midl/-error)枚举）。

### <a name="check-reference-pointers"></a>检查参考指针

检查引用指针为非空[（/错误](/windows/win32/midl/-error)参考）。

### <a name="check-stub-data"></a>检查存根数据

发出其他检查，检查服务器端存根数据的有效性[（/错误](/windows/win32/midl/-error)stub_data）。

### <a name="prepend-with-abi-namespace"></a>使用"ABI"命名空间进行预写

将"ABI"命名空间准备到所有类型的。  [（/ns_prefix](/windows/win32/midl/-ns-prefix)）。

### <a name="validate-parameters"></a>验证参数

生成其他信息以验证参数[（/robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)）。

### <a name="struct-member-alignment"></a>结构成员对齐

指定目标系统中结构 （/ZpN） 中的封装水平。

**选择**

- **未设置**- 未设置
- **1 字节**- Zp1
- **2 字节**- Zp2
- **4 字节**- Zp4
- **8 字节**- Zp8

### <a name="redirect-output"></a>重定向输出

将输出从屏幕重定向到文件[（/o](/windows/win32/midl/-o)文件）。

### <a name="minimum-target-system"></a>最小目标系统

设置最小目标系统[（/目标](/windows/win32/midl/-target)STRING）。
