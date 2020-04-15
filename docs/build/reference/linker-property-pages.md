---
title: “链接器”属性页
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 2f2068c6c51fc6bf4e4104213e946e243fc6df2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336585"
---
# <a name="linker-property-pages"></a>“链接器”属性页

以下属性位于**项目** > **属性** > **配置属性** > **链接器**下。 有关链接器的详细信息，请参阅 CL[调用链接器](cl-invokes-the-linker.md)和[链接器选项](linker-options.md)。

## <a name="general-property-page"></a>“常规属性”页

### <a name="output-file"></a>输出文件

[/OUT](out-output-file-name.md)选项将覆盖链接器创建的程序的默认名称和位置。

### <a name="show-progress"></a>显示进度

打印链接器进度消息

**选择**

- **未设置**- 无详细性。
- **显示所有进度消息**- 显示所有进度消息。
- **对于搜索的库**- 显示显示显示仅搜索的库的进度消息。
- **关于优化链接期间的 COMDAT 折叠**- 在优化链接期间显示有关 COMDAT 折叠的信息。
- **关于优化链接期间删除的数据**- 显示有关优化链接期间删除的函数和数据的信息。
- **关于与 SEH 不兼容的模块**- 显示与安全异常处理不兼容的模块的信息。
- **关于与托管代码相关的链接器活动**- 显示有关链接器活动的信息，这些活动与托管代码相关。

### <a name="version"></a>版本

[/VERSION](version-version-information.md)选项告诉链接器将版本号放在 .exe 或 .dll 文件的标头中。 使用 DUMPBIN/HEADERS 查看"可选标题"的图像版本字段以查看 **/VERSION**的效果。

### <a name="enable-incremental-linking"></a>启用增量链接

启用增量链接。 [（/增量](incremental-link-incrementally.md)，/增量：否）

### <a name="suppress-startup-banner"></a>取消显示启动版权标志

[/NOLOGO](nologo-suppress-startup-banner-linker.md)选项可防止显示版权消息和版本号。

### <a name="ignore-import-library"></a>Ignore Import Library

此属性指示链接器不要将基于该版本生成的任何 .lib 输出链接到任何相关项目。 它允许项目系统处理生成时不生成 .lib 文件的 .dll 文件。 如果项目依赖于创建 DLL 的另一个项目，则项目系统会自动链接该子项目生成的 .lib 文件。 在生成 COM DLL 或仅资源 DLL 的项目中，此属性可能没有必要，因为这些 DLL 没有任何有意义的导出。 如果 DLL 没有导出，则链接器不会生成 .lib 文件。 如果不存在导出 .lib 文件，并且项目系统告诉链接器与缺少的 DLL 链接，则链接将失败。 使用 Ignore Import Library 属性解决此问题****。 当设置为 **"是**"时，项目系统将忽略 .lib 文件的存在或不存在，并导致依赖于此项目的任何项目不链接到不存在的 .lib 文件。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>。

### <a name="register-output"></a>Register Output

在生成输出上运行 `regsvr32.exe /s $(TargetPath)`，仅在 .dll 项目上有效。 对于 .exe 项目，则忽略此属性。 要注册 .exe 输出，请在配置上设置生成后事件以执行注册 .exe 文件始终所需的自定义注册。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>。

### <a name="per-user-redirection"></a>Per-user Redirection

传统上，Visual Studio 中的注册是在 HKEY_CLASSES_ROOT (HKCR) 中完成的。 如果使用 Windows Vista 及更高版本的操作系统，则必须在提升模式下运行 Visual Studio 才能访问 HKCR。 开发人员并不总是希望在提升模式下运行，但仍必须使用注册。 每个用户重定向允许您注册，而无需在提升模式下运行。

Per-user Redirection 强制将任何对 HKCR 的写入重定向到 HKEY\_CURRENT\_USER (HKCU)。 如果关闭了 Per-user Redirection，当程序试图写入到 HKCR 时，可能导致[项目生成错误 PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md)。

### <a name="additional-library-directories"></a>附加库目录

允许用户重写环境库路径。 [（/LIBPATH](libpath-additional-libpath.md)：文件夹）

### <a name="link-library-dependencies"></a>链接库依赖项

指定是否链接由依赖项目生成的 .lib 文件。 通常，您希望在 .lib 文件中链接，但某些 DLL 可能不是这样。

也可通过提供文件名和相对路径来指定 .obj 文件，如“..\\..\MyLibProject\MyObjFile.obj”。 如果 .obj 文件的源代码#includes预编译的标头（例如 pch.h），则 pch.obj 文件与 MyObjFile.obj 位于同一文件夹中。您还必须添加 pch.obj 作为附加依赖项。

### <a name="use-library-dependency-inputs"></a>使用库依赖项输入

指定在项目依赖项的库输出中链接时，是否将输入用于图书管理员工具，而不是库文件本身。 在大型项目中，当依赖项目生成 .lib 文件时，将禁用增量链接。 如果有许多依赖项目生成 .lib 文件，则生成应用程序可能需要很长时间。 当此属性设置为 **"是**"时，项目系统将链接在由从属项目生成的 .obj 文件中的 .obj 文件中，从而启用增量链接。

有关如何访问**常规**链接器属性页的信息，请参阅在 Visual [Studio 中设置C++编译器和生成属性](../working-with-project-properties.md)。

### <a name="link-status"></a>链接状态

指定链接器是否应显示进度指示器，显示链接已完成的百分比。 默认值为不显示此状态信息。 [（/LTCG](ltcg-link-time-code-generation.md)：状态*LTCG：无状态）

### <a name="prevent-dll-binding"></a>防止 DLL 绑定

[/ALLOWBIND](allowbind-prevent-dll-binding.md)：NO 在 DLL 的标头中设置一个位，指示 Bind.exe 不允许绑定图像。 如果 DLL 已经进行数字签名（绑定使签名无效），可能不需要绑定 DLL。

### <a name="treat-linker-warning-as-errors"></a>将链接器警告视为错误

[/WX](wx-treat-linker-warnings-as-errors.md)会导致在链接器生成警告时不会生成输出文件。

### <a name="force-file-output"></a>强制文件输出

[/FORCE](force-force-file-output.md)选项告诉链接器创建 .exe 文件或 DLL，即使符号被引用但未定义，或者是乘以定义的。 它可能创建无效的 .exe 文件。

**选择**

- **启用**- /FORCE，没有参数意味着多重和未解决。
- **仅将定义的符号相乘**- 使用 /FORCE：MULTI 创建输出文件，即使 LINK 为符号找到多个定义也是如此。
- **仅未定义符号**- 使用 /FORCE：UNRESOLVED创建输出文件，无论 LINK 是否找到未定义的符号。 /FORCE：如果入口点符号未解析，则忽略 UNRESOLVED。

### <a name="create-hot-patchable-image"></a>创建热可修补图像

准备用于热修补的图像。

**选择**

- **已启用**- 准备用于热修补的图像。
- **仅限 X86 图像**- 准备 X86 图像进行热修补。
- **仅限 X64 图像**- 准备 X64 图像进行热修补。
- **仅 Itanium 图像**- 准备用于热修补的 Itanium 图像。

### <a name="specify-section-attributes"></a>指定节属性

[/SECTION](section-specify-section-attributes.md)选项更改节的属性，在编译节的 .obj 文件时重写属性集。

## <a name="input-property-page"></a>输入属性页

### <a name="additional-dependencies"></a>附加依赖项

指定要添加到链接命令行的其他项，例如*内核32.lib*。

### <a name="ignore-all-default-libraries"></a>忽略所有默认库

[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)选项告诉链接器在解析外部引用时从它搜索的库列表中删除一个或多个默认库。

### <a name="ignore-specific-default-libraries"></a>忽略特定默认库

指定一个或多个要忽略的默认库的名称。 使用分号分隔多个库。 （/NODEFAULTLIB：[名称，名称，...]

### <a name="module-definition-file"></a>模块定义文件

[/DEF](def-specify-module-definition-file.md)选项将模块定义文件 （.def） 传递给链接器。 只能指定一个 .def 文件到 LINK。

### <a name="add-module-to-assembly"></a>将模块添加到装配体

[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)选项允许您向程序集添加模块引用。 模块中的类型信息将不适用于添加模块引用的程序集程序。 但是，模块中的类型信息将可用于引用程序集的任何程序。

### <a name="embed-managed-resource-file"></a>嵌入托管资源文件

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)在输出文件中嵌入资源文件。

### <a name="force-symbol-references"></a>强制符号引用

[/INCLUDE](include-force-symbol-references.md)选项告诉链接器向符号表添加指定的符号。

### <a name="delay-loaded-dlls"></a>延迟加载的 DLL

[/DELAYLOAD](delayload-delay-load-import.md)选项会导致 DLL 加载延迟。 dll 名称指定用于延迟加载的 DLL。

### <a name="assembly-link-resource"></a>程序集链接资源

[/ASSEMBLYLINKRESOURCE 选项](assemblylinkresource-link-to-dotnet-framework-resource.md)在输出文件中创建指向 .NET 框架资源的链接;资源文件未放置在输出文件中。

## <a name="manifest-file-property-page"></a>清单文件属性页

### <a name="generate-manifest"></a>生成清单

[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md)指定链接器应创建并排清单文件。

### <a name="manifest-file"></a>清单文件

[/MANIFESTFILE](manifestfile-name-manifest-file.md)允许您更改清单文件的默认名称。 清单文件的默认名称是附加 .manifest 的文件名。

### <a name="additional-manifest-dependencies"></a>其他清单依赖项

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)允许您指定将放置在清单文件的依赖项部分的属性。

### <a name="allow-isolation"></a>允许隔离

指定清单查找的行为。 [（/允许隔离](allowisolation-manifest-lookup.md)：否）

### <a name="enable-user-account-control-uac"></a>启用用户帐户控制 （UAC）

指定是否启用用户帐户控制。  （/***************************************[/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)

### <a name="uac-execution-level"></a>UAC 执行级别

使用用户帐户控件运行时为应用程序指定请求的执行级别。  （/MANIFESTUAC：级别=值*）

**选择**

- **asInvoker** - UAC 执行级别：作为调用器。
- **最高可用 -** UAC 执行级别：最高可用。
- **需要管理员**- UAC 执行级别：需要管理员。

### <a name="uac-bypass-ui-protection"></a>UAC 旁路 UI 保护

指定是否绕过桌面上其他窗口的用户界面保护级别。  仅为辅助功能应用程序将此属性设置为"是"。  [（/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)：uiAccess_true = 假]）

## <a name="debugging-property-page"></a>“调试”属性页

### <a name="generate-debug-info"></a>生成调试信息

此选项允许为 .exe 文件或 DLL 创建调试信息。

**选择**

- **否**- 不生成调试信息。
- **生成调试信息**- 创建一个完整的程序数据库 （PDB），非常适合分发到 Microsoft 符号服务器。
- **生成针对更快链接优化的调试信息**- 生成程序数据库 （PDB），非常适合编辑链接-调试周期。
- **生成针对共享和发布优化的调试信息**- 生成程序数据库 （PDB），非常适合编辑链接-调试周期。

### <a name="generate-program-database-file"></a>生成程序数据库文件

默认情况下，当指定[/DEBUG](debug-generate-debug-info.md)时，链接器将创建一个程序数据库 （PDB），该数据库包含调试信息。 PDB 的默认文件名具有程序的基本名称和扩展名 .pdb。

### <a name="strip-private-symbols"></a>剥离专用符号

[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)选项在使用生成 PDB 文件的任何编译器或链接器选项（/DEBUG、/Z7、/Zd 或 /Zi）构建程序映像时创建第二个程序数据库 （PDB） 文件。

### <a name="generate-map-file"></a>生成映射文件

[/MAP](map-generate-mapfile.md)选项告诉链接器创建地图文件。

### <a name="map-file-name"></a>映射文件名

地图文件的用户指定名称。 它将替换默认名称。

### <a name="map-exports"></a>地图导出

[/MAPINFO](mapinfo-include-information-in-mapfile.md)选项告诉链接器在地图文件中包含指定的信息，如果指定 /MAP 选项，将创建该映射文件。 EXPORT 告诉链接器包括导出的函数。

### <a name="debuggable-assembly"></a>可调试程序集

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)发出调试属性属性，通过调试信息跟踪并禁用 JIT 优化。

## <a name="system-property-page"></a>系统属性页

### <a name="subsystem"></a>子系统

[/SUBSYSTEM](subsystem-specify-subsystem.md)选项告诉操作系统如何运行 .exe 文件。 子系统的选择会影响链接器将选择的入口点符号（或入口点函数）。

**选择**

- **未设置**- 未设置子系统。
- **控制台**- Win32字符模式应用程序。 控制台应用程序由操作系统提供控制台。 如果定义了主控或 wmain，则"CONSOLE"是默认值。
- **Windows** - 应用程序不需要控制台，可能是因为它创建自己的窗口与用户交互。 如果定义了 WinMain 或 wWinMain，则"WINDOWS"是默认值。
- **本机**- Windows NT 的设备驱动程序。 如果指定 /DRIVER：WDM，则本机为默认值。
- **EFI 应用程序**- EFI 应用程序。
- **EFI 引导服务驱动程序**- EFI 引导服务驱动程序。
- **EFI ROM** - EFI ROM。
- **EFI 运行时**- EFI 运行时。
- **POSIX** - 在 Windows NT 中使用 POSIX 子系统运行的应用程序。

### <a name="minimum-required-version"></a>最低所需版本

指定子系统的最小所需版本。 参数是范围 0 到 65，535 中的十进制数字。

### <a name="heap-reserve-size"></a>堆保留大小

指定虚拟内存中的堆分配总大小。 默认值为 1 MB。    [（/HEAP：](heap-set-heap-size.md)保留）

### <a name="heap-commit-size"></a>堆提交大小

指定物理内存中的堆分配总大小。 默认值为 4 KB。    [（/HEAP](heap-set-heap-size.md)：保留，提交）

### <a name="stack-reserve-size"></a>堆栈保留大小

指定虚拟内存中的堆栈分配总大小。 默认值为 1 MB。     [（/STACK：](stack-stack-allocations.md)保留）

### <a name="stack-commit-size"></a>堆栈提交大小

指定物理内存中的总堆栈分配大小。 默认值为 4 KB。     [（/STACK：](stack-stack-allocations.md)保留，提交）

### <a name="enable-large-addresses"></a>启用大地址

[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)选项告诉链接器应用程序可以处理大于 2 GB 的地址。 默认情况下，/LARGEADDRESSAWARE：如果在链接器线路上未以其他方式指定 /LARGEADDRESSAWARE，则启用"否"。

### <a name="terminal-server"></a>终端服务器

[/TSAWARE](tsaware-create-terminal-server-aware-application.md)选项在程序图像的可选标题中的IMAGE_OPTIONAL_HEADER Dll特色字段中设置标志。 当设置此标志后，终端服务器将不会向应用程序进行某些更改。

### <a name="swap-run-from-cd"></a>从 CD 交换运行

[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)选项告诉操作系统首先将链接器输出复制到交换文件，然后从那里运行映像。 此选项是 Windows NT 4.0（及更高版本）功能。 指定**CD**后，操作系统会将可移动磁盘上的映像复制到页面文件，然后加载它。

### <a name="swap-run-from-network"></a>从网络交换运行

[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)选项告诉操作系统首先将链接器输出复制到交换文件，然后从那里运行映像。 此选项是 Windows NT 4.0（及更高版本）功能。 如果指定**了 NET，** 操作系统将首先将二进制映像从网络复制到交换文件，并从那里加载该文件。 此选项可用于通过网络运行应用程序。

### <a name="driver"></a>驱动程序

使用[/DRIVER](driver-windows-nt-kernel-mode-driver.md)链接器选项生成 Windows NT 内核模式驱动程序。

**选择**

- **未设置**- 默认驱动程序设置。
- **驱动程序**- 驱动程序
- **仅限 UP** - /DRIVER：UPONLY 使链接器将IMAGE_FILE_UP_SYSTEM_ONLY位添加到输出标头中的特征，以指定它是单处理器 （UP） 驱动程序。 操作系统将拒绝在多处理器 （MP） 系统上加载 UP 驱动程序。
- **WDM** - /DRIVER：WDM 使链接器在可选标头的 Dll特征字段中设置IMAGE_DLLCHARACTERISTICS_WDM_DRIVER位。

## <a name="optimization-property-page"></a>优化属性页

### <a name="references"></a>reference

[/OPT](opt-optimizations.md)：REF 消除了从未引用的函数和/或数据，而 /OPT：NOREF 保留从未引用的函数和/或数据。

### <a name="enable-comdat-folding"></a>启用 COMDAT 折叠

使用[/OPT](opt-optimizations.md)：ICF\[[迭代] 执行相同的 COMDAT 折叠。

### <a name="function-order"></a>功能顺序

[/ORDER](order-put-functions-in-order.md)选项告诉 LINK 以预定的顺序将某些 COMDAT 放入映像中来优化程序。 LINK 在图像中的每个部分中按指定顺序放置函数。

### <a name="profile-guided-database"></a>配置文件引导数据库

为配置文件引导优化指定 .pgd 文件。 （[/PGD](pgd-specify-database-for-profile-guided-optimizations.md)）

### <a name="link-time-code-generation"></a>链接时间代码生成

指定链接时间代码生成。 （[/LTCG](ltcg-link-time-code-generation.md)）

**选择**

- **默认值**- 默认 LTCG 设置。
- **使用快速链接时间代码生成**- 使用链接时间代码生成与[/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。
- **使用链接时间代码生成**- 使用[链接时间代码生成](ltcg-link-time-code-generation.md)。
- **配置文件引导优化 - 仪器**- 使用[:PGINSTRUMENT 的配置文件引导优化](../profile-guided-optimizations.md)。
- **配置文件引导优化 - 优化**- 指定链接器应使用运行检测的二进制文件后创建的配置文件数据来创建优化的图像。
- **配置文件引导优化 - 更新**- 允许并跟踪从 :PGINSTRUMENT 阶段中指定的内容添加或修改的输入文件列表。

## <a name="embedded-idl-property-page"></a>嵌入式 IDL 属性页

### <a name="midl-commands"></a>MIDL 命令

指定 MIDL 命令行选项。 （[/MIDL](midl-specify-midl-command-line-options.md):@responsefile）

### <a name="ignore-embedded-idl"></a>忽略嵌入式 IDL

[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)选项指定源代码中的任何 IDL 属性都不应处理到 .idl 文件中。

### <a name="merged-idl-base-file-name"></a>合并的 IDL 基本文件名

[/IDLOUT](idlout-name-midl-output-files.md)选项指定 .idl 文件的名称和扩展名。

### <a name="type-library"></a>类型库

[/TLBOUT](tlbout-name-dot-tlb-file.md)选项指定 .tlb 文件的名称和扩展名。

### <a name="typelib-resource-id"></a>类型 Lib 资源 ID

允许您指定链接器生成的类型库的资源 ID。 [（/TLBID](tlbid-specify-resource-id-for-typelib.md)：id）

## <a name="windows-metadata-property-page"></a>窗口元数据属性页

### <a name="generate-windows-metadata"></a>生成 Windows 元数据

启用或禁用生成 Windows 元数据。

**选择**

- **是**- 启用生成 Windows 元数据文件。
- **否**- 禁用生成 Windows 元数据文件。

### <a name="windows-metadata-file"></a>窗口元数据文件

[/WINMDFILE](winmdfile-specify-winmd-file.md)选项开关。

### <a name="windows-metadata-key-file"></a>Windows 元数据密钥文件

指定键或密钥对以对 Windows 元数据进行签名。 [（/温德基文件](winmdkeyfile-specify-winmd-key-file.md)：文件名）

### <a name="windows-metadata-key-container"></a>窗口元数据密钥容器

指定一个键容器来对 Windows 元数据进行签名。 [（/温德基：](winmdkeycontainer-specify-key-container.md)姓名）

### <a name="windows-metadata-delay-sign"></a>窗口元数据延迟符号

部分签名 Windows 元数据。 如果您只想将公钥放在 Windows 元数据中，请使用[/WINMDDELAYSIGN。](winmddelaysign-partially-sign-a-winmd.md) 默认值为 /WINMDDELAYSIGN：否。

## <a name="advanced-property-page"></a>高级属性页

### <a name="entry-point"></a>入口点

[/ENTRY](entry-entry-point-symbol.md)选项指定入口点函数作为 .exe 文件或 DLL 的起始地址。

### <a name="no-entry-point"></a>无入口点

创建仅资源 DLL 需要[/NOENTRY](noentry-no-entry-point.md)选项。使用此选项可防止 LINK 将引用`_main`链接到 DLL。

### <a name="set-checksum"></a>设置校验和

[/RELEASE](release-set-the-checksum.md)选项在 .exe 文件的头部设置校验和。

### <a name="base-address"></a>基址

为程序设置基址。 [（/BASE](base-base-address.md)：地址\[，大小] |@filename"键"）

### <a name="randomized-base-address"></a>随机基本地址

随机基本地址。 [（/动态基础](dynamicbase-use-address-space-layout-randomization.md)\[：否]）

### <a name="fixed-base-address"></a>固定基本地址

创建只能在其首选基址加载的程序。 [（/固定](fixed-fixed-base-address.md)\[：否*）

### <a name="data-execution-prevention-dep"></a>数据执行保护 (DEP)

将可执行文件标记为已测试为与 Windows 数据执行预防功能兼容。 [（/NXcompat](nxcompat-compatible-with-data-execution-prevention.md)\[：否]）

### <a name="turn-off-assembly-generation"></a>关闭组件生成

[/NOASSEMBLY](noassembly-create-a-msil-module.md)选项告诉链接器为当前输出文件创建图像，而不使用 .NET Framework 程序集。

### <a name="unload-delay-loaded-dll"></a>卸载加载的延迟 DLL

**UNLOAD**限定符告诉延迟加载帮助器函数以支持 DLL 的显式卸载。 [（/延迟](delay-delay-load-import-settings.md)：卸载）

### <a name="nobind-delay-loaded-dll"></a>未绑定延迟加载 DLL

**NOBIND**限定符告诉链接器不要在最终图像中包含可绑定的 IAT。 默认值是为延迟加载的 DLL 创建可绑定的 IAT。 [（/延迟](delay-delay-load-import-settings.md)：不绑定）

### <a name="import-library"></a>导入库

重写默认的导入库名。 [（/IMPLIB](implib-name-import-library.md)：文件名）

### <a name="merge-sections"></a>合并节

[/MERGE](merge-combine-sections.md)选项将第一部分（来自）和第二部分（到）合并，将生成的部分命名为 例如，/合并：.rdata_.text。

### <a name="target-machine"></a>目标机器

[/MACHINE](machine-specify-target-platform.md)选项指定程序的目标平台。

**选择**

- **未设置**
- **机器ARM**
- **机器ARM64**
- **机机**
- **机器IA64**
- **机器MIPS**
- **机器MIPS16**
- **机器MIPSFPU**
- **机器MIPSFPU16**
- **机器SH4**
- **机器**
- **机器X64**
- **机器X86**

### <a name="profile"></a>配置文件

生成一个可与“性能工具”探查器结合使用的输出文件。 需要设置生成调试信息 （/[/DEBUG）。](debug-generate-debug-info.md) （[/简介](profile-performance-tools-profiler.md)）

### <a name="clr-thread-attribute"></a>CLR 线程属性

显式指定 CLR 程序入口点的线程属性。

**选择**

- **MTA 线程属性**- 将 MTAThreadAttribute 属性应用于程序的入口点。
- **STA 线程属性**- 将 STAThreadAttribute 属性应用于程序的入口点。
- **默认线程属性**- 与未指定[/CLRTHREAD 属性](clrthreadattribute-set-clr-thread-attribute.md)相同。 让通用语言运行时 （CLR） 设置默认线程属性。

### <a name="clr-image-type"></a>CLR 图像类型

设置 CLR 映像的类型（IJW、纯或安全）。

**选择**

- **强制 IJW 图像**
- **强制纯 IL 图像**
- **强制安全 IL 图像**
- **默认图像类型**

### <a name="key-file"></a>密钥文件

指定键或键对以对程序集进行签名。 [（/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)：文件名）

### <a name="key-container"></a>密钥容器

指定要对程序集进行签名的键容器。 [（/键式](keycontainer-specify-a-key-container-to-sign-an-assembly.md)：姓名）

### <a name="delay-sign"></a>延迟符号

对程序集进行部分签名。 如果只想将公钥放在程序集中，请使用[/DELAYSIGN。](delaysign-partially-sign-an-assembly.md) 默认值为 /DELAYSIGN：否。

### <a name="clr-unmanaged-code-check"></a>CLR 非托管代码检查

[/CLRUN管理代码检查](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)指定链接器是否将禁止解压缩 Un 托管代码安全属性应用于从托管代码链接到本机 DLL 的 Pler 生成的 PInvoke 调用。

### <a name="error-reporting"></a>错误报告

允许您直接向 Visual C++ 团队提供内部编译器错误(ICE)信息。

**选择**

- **立即提示**- 立即提示。
- **下一个登录队列**- 下一个登录队列。
- **发送错误报告**- 发送错误报告。
- **无错误报告**- 无错误报告。

### <a name="sectionalignment"></a>SectionAlignment

[/ALIGN](align-section-alignment.md)选项指定程序线性地址空间中每个部分的对齐方式。 数字参数以字节为单位，并且必须是 2 的电源。

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>保留 PInvoke 调用的最后错误代码

[/CLRSUPPORTLASTERROR（](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)默认情况下处于打开状态）保留了通过 P/Invoke 机制调用的函数的最后错误代码，该机制允许您从使用 /clr 编译的代码调用 DLLS 中的本机函数。

**选择**

- **已启用**- 启用 CLR 支持Last错误。
- **禁用**- 禁用 CLR 支持Last错误。
- **仅限系统 Dlls** - 仅启用 CLRSupportLastError。

### <a name="image-has-safe-exception-handlers"></a>映像具有安全异常处理程序

指定[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)后，链接器仅当还可以生成映像的安全异常处理程序的表时才会生成映像。 此表为操作系统指定异常处理程序对映像有效。
