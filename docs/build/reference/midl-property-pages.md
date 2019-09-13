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
ms.openlocfilehash: e9c9cb75d326642c86405992a4bf9d7da9e578df
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927697"
---
# <a name="midl-property-pages"></a>“MIDL”属性页

MIDL 属性页作为上的项属性提供。使用 COM 的C++项目中的 IDL 文件。 使用它们来配置[MIDL 编译器](/windows/win32/midl/using-the-midl-compiler-2)。 有关如何以编程方式访问 C++ 项目的 MIDL 选项的信息，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool> 对象。 另请参阅[常规 MIDL 命令行语法](/windows/win32/midl/general-midl-command-line-syntax)。

## <a name="general-property-page"></a>"常规属性" 页

### <a name="preprocessor-definitions"></a>预处理器定义

指定一个或多个定义, 包括 MIDL 宏 ([/D](/windows/win32/midl/-d))\[macros\]).

### <a name="additional-include-directories"></a>附加包含目录

指定要添加到包含路径（[/i](/windows/win32/midl/-i)\[路径\]）中的一个或多个目录。

### <a name="additional-metadata-directories"></a>其他元数据目录

指定包含 Windows Foundation 文件（[/metadata_dir](/windows/win32/midl/-metadata-dir) \[路径\]）的目录。

### <a name="enable-windows-runtime"></a>启用 Windows 运行时

启用 Windows 运行时语义以创建 Windows 元数据文件（[/winrt](/windows/win32/midl/-winrt)）。

### <a name="ignore-standard-include-path"></a>忽略标准包含路径

忽略当前和包含目录（[/no_def_idir](/windows/win32/midl/-no-def-idir)）。

### <a name="mktyplib-compatible"></a>Mktyplib.exe 兼容

强制与 mktyplib.exe 2.03 版兼容（[/mktyplib203](/windows/win32/midl/-mktyplib203)）。

### <a name="warning-level"></a>警告级别

选择 MIDL 代码错误（[/w](/windows/win32/midl/-w)）的严格性。

**方案**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>将警告视为错误

允许 MIDL 将所有警告视为错误（[/wx](/windows/win32/midl/-wx)）。

### <a name="suppress-startup-banner"></a>取消显示启动版权标志

禁止显示启动版权标志和信息消息（[/nologo](/windows/win32/midl/-nologo)）。

### <a name="c-compiler-char-type"></a>C 编译器字符类型

指定将用于编译所生成代码的 C 编译器的默认字符类型。 （[/char](/windows/win32/midl/-char)已签名 | 未签名 | ascii7）。

**方案**

- **签名**签名
- **无**符号无符号
- **Ascii** -ascii

### <a name="target-environment"></a>目标环境

指定目标环境（[/env](/windows/win32/midl/-env) arm32 | win32 | ia64 | x64）。

**方案**

- **未设置**-Win32
- **Microsoft Windows 32 位**-Win32
- **Itanium 上的 Microsoft Windows 64 位**-IA64
- **Microsoft WINDOWS arm** -arm
- **Microsoft WINDOWS ARM64** -ARM64
- **X64 上的 Microsoft Windows 64 位**-x64

### <a name="generate-stubless-proxies"></a>生成无存根代理

生成具有对象接口的扩展和无存根代理的完全解释的存根（[/Oicf](/windows/win32/midl/-oi)， [/Oif](/windows/win32/midl/-oi) ）。

### <a name="suppress-compiler-warnings"></a>取消显示编译器警告

禁止显示编译器警告消息（[/no_warn](/windows/win32/midl/-no-warn)）。

### <a name="application-configuration-mode"></a>应用程序配置模式

允许在 IDL 文件中选择 ACF 属性（[/app_config](/windows/win32/midl/-app-config)）。

### <a name="locale-id"></a>区域设置 ID

指定输入文件的 LCID、文件名和目录路径（[/Lcid](/windows/win32/midl/-lcid) DECIMAL）。

### <a name="multi-processor-compilation"></a>多处理器编译

同时运行多个实例。

## <a name="output-property-page"></a>输出属性页

### <a name="output-directory"></a>输出目录

指定输出目录（[/out](/windows/win32/midl/-out) [目录]）。

### <a name="metadata-file"></a>元数据文件

指定生成的元数据文件的名称（[/winmd](/windows/win32/midl/-winmd) filename）。

### <a name="header-file"></a>标头文件

指定生成的标头文件（[/h](/windows/win32/midl/-h)文件名）的名称。

### <a name="dlldata-file"></a>Dlldata.c 文件

指定 DLLDATA.C 文件的名称（[/dlldata](/windows/win32/midl/-dlldata) filename）。

### <a name="iid-file"></a>IID 文件

指定接口标识符文件的名称（[/iid](/windows/win32/midl/-iid) filename）。

### <a name="proxy-file"></a>代理文件

指定代理文件的名称（[/proxy](/windows/win32/midl/-proxy) filename）。

### <a name="generate-type-library"></a>生成类型库

指定不生成类型库（[/notlb] 表示不生成）。

### <a name="type-library"></a>类型库

指定类型库文件的名称（[/tlb](/windows/win32/midl/-tlb) filename）。

### <a name="generate-client-stub-files"></a>生成客户端存根文件

仅生成客户端存根（stub）文件（[/client](/windows/win32/midl/-client) [stub | none]）。

**方案**

- **存根**-存根
- **无**-无

### <a name="generate-server-stub-files"></a>生成服务器存根文件

仅生成服务器存根（stub）文件（[/server](/windows/win32/midl/-server) [stub | none]）。

**方案**

- **存根**-存根
- **无**-无

### <a name="client-stub-file"></a>客户端存根文件

指定客户端存根（stub）文件（[/cstub](/windows/win32/midl/-cstub) [文件]）。

### <a name="server-stub-file"></a>服务器存根文件

指定服务器存根（stub）文件（[/sstub](/windows/win32/midl/-sstub) [文件]）。

### <a name="type-library-format"></a>类型库格式

指定类型库文件格式（[/oldtlb |/newtlb]）。

**方案**

- **NewFormat** -新格式
- **OldFormat** -旧格式

## <a name="advanced-property-page"></a>"高级" 属性页

### <a name="c-preprocess-options"></a>C 预处理选项

指定要传递给 C 编译器预处理器（[/cpp_opt](/windows/win32/midl/-cpp-opt)开关）的开关。

### <a name="undefine-preprocessor-definitions"></a>取消定义预处理器定义

指定一个或多个取消指定，包括 MIDL 宏（[/u](/windows/win32/midl/-U) [宏]）。

### <a name="enable-error-checking"></a>启用错误检查

选择错误检查选项（[/error all | none]）。

**方案**

- **EnableCustom** -所有
- **全部**-所有
- **无**-无

### <a name="check-allocations"></a>检查分配

检查内存不足错误（[/error](/windows/win32/midl/-error)分配）。

### <a name="check-bounds"></a>检查边界

检查大小与传输长度规范（[/error](/windows/win32/midl/-error) bounds_check）。

### <a name="check-enum-range"></a>检查枚举范围

检查枚举值是否在允许的范围内（[/error](/windows/win32/midl/-error) enum）。

### <a name="check-reference-pointers"></a>检查引用指针

检查引用指针是否为非 null （[/error](/windows/win32/midl/-error) ref）。

### <a name="check-stub-data"></a>检查存根（Stub）数据

发出对服务器端存根（stub）数据有效性的其他检查（[/error](/windows/win32/midl/-error) stub_data）。

### <a name="prepend-with-abi-namespace"></a>预置 "ABI" 命名空间

在所有类型前面预置 "ABI" 命名空间。  （[/ns_prefix](/windows/win32/midl/-ns-prefix)）。

### <a name="validate-parameters"></a>验证参数

生成其他信息以验证参数（[/robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)）。

### <a name="struct-member-alignment"></a>结构成员对齐

指定目标系统中的结构的封装级别（/ZpN）。

**方案**

- **未设置**-未设置
- **1 字节**-Zp1
- **2 字节**-Zp2
- **4 字节**-Zp4
- **8 字节**-Zp8

### <a name="redirect-output"></a>重定向输出

将输出从屏幕重定向到文件（[/o](/windows/win32/midl/-o)文件）。

### <a name="minimum-target-system"></a>最低目标系统

设置最低目标系统（[/Target](/windows/win32/midl/-target) STRING）。



