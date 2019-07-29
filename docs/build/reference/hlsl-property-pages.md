---
title: “HLSL”属性页
ms.date: 07/24/2019
ms.assetid: 0c65f5ec-a2a5-4f5b-8d4c-fa57113a5a1d
f1_keywords:
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.SuppressStartupBanner
- VC.Project.FXCompilerTool.EntryPointName
- VC.Project.FXCompilerTool.TreatWarningAsError
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.AllResourcesBound
- VC.Project.FXCompilerTool.EnableUnboundedDescriptorTables
- VC.Project.FXCompilerTool.SetRootSignature
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.AdditionalOptionsPage
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.AssemblerOutputFile
- VC.Project.FXCompilerTool.CompileD2DCustomEffect
- VC.Project.FXCompilerTool.MultiProcFXC
ms.openlocfilehash: a45ae433e5adaa8aeaf32215d4af7ad0a247af04
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606410"
---
# <a name="hlsl-compiler-property-pages"></a>HLSL 编译器属性页

可以使用 HLSL 编译器 (fxc.exe) 属性页来配置单个 HLSL 着色器文件生成的方式。 还可以使用 "**命令行**" 属性页的 "**其他选项**" 属性指定 HLSL 编译器的命令行参数。这包括无法使用 HLSL 属性页的其他属性进行配置的参数。 有关 HLSL 编译器的其他信息，请参阅[效果编译器工具](https://go.microsoft.com/fwlink/p/?LinkID=258285&clcid=0x409)

## <a name="hlsl-general-property-page"></a>HLSL 常规属性页

### <a name="additional-include-directories"></a>附加包含目录

指定一个或多个要添加到包含路径中的目录；存在多个目录时，请用分号分隔。 (/I [路径])

### <a name="entrypoint-name"></a>入口点名称

指定着色器的入口点名称 (/E [name])

### <a name="disable-optimizations"></a>禁用优化

若要启用优化，则为“是(/Od)”；否则为“否”。 默认情况下，“调试”配置的值为“是(/Od)”，而“发布”配置的值为“否”。

HLSL 编译器的“/Od”命令行参数隐式应用“/Gfp”命令行参数，但输出可能与通过显示传递“/Od”和“/Gfp”命令行参数生成的输出不同。

### <a name="enable-debugging-information"></a>启用调试信息

若启用调试信息，则为“是(/Od)”；否则为“否”。 默认情况下，“调试”配置的值为“是(/Zi)”，而“发布”配置的值为“否”。

### <a name="shader-type"></a>着色器类型

指定着色器类型。 不同种类的着色器实现图形管道的不同部分。 某些类型的着色器仅可用于较新的着色器模型（由“着色器模型”属性指定），例如，计算着色器在着色器模型 5 中引入。

此属性对应于 HLSL 编译器的 **/T \[type]_\[model]** 命令行参数的 **\[type]** 部分。 “着色器模型”属性指定参数的“[model]”部分。

**方案**

- **效果**
- **顶点着色器**
- **像素着色器**
- **几何着色器**
- **凸着色器**
- **域着色器**
- **计算着色器**
- **Library**
- **生成根签名对象**

### <a name="shader-model"></a>着色器模型

指定着色器模型。 不同的着色器模型具有不同的功能。 一般情况下，较新的着色器模型提供扩展功能，但需要更新式图形硬件来运行着色器代码。 某些类型的着色器（由“着色器类型”属性指定）仅可用于较新的着色器模型，例如，计算着色器在着色器模型 5 中引入。

此属性对应于 HLSL 编译器的 **/T \[type]_\[model]** 命令行参数的 **\[model]** 部分。 “着色器类型”属性指定参数的“[type]”部分。

### <a name="all-resources-bound"></a>所有资源已绑定

编译器将假定在着色器执行 (/all_resources_bound) 的持续时间内, 着色器可能引用的所有资源都已绑定并且处于良好状态。 适用于着色器模型 5.1 及更高版本。

### <a name="enable-unbounded-descriptor-tables"></a>启用未绑定的描述符表

通知编译器着色器可能包含具有无限范围 (/enable_unbounded_descriptor_tables) 的资源数组的声明。 适用于着色器模型 5.1 及更高版本。

### <a name="set-root-signature"></a>设置根签名

将根签名附加到着色器字节码 (/setrootsignature)。 适用于着色器模型 5.0 及更高版本。

### <a name="preprocessor-definitions"></a>预处理器定义

添加一个或多个预处理器符号定义以应用于 HLSL 源代码文件。 使用分号来隔开符号定义。

此属性对应于 HLSL 编译器的 /D \[definitions] 命令行参数。

### <a name="compile-a-direct2d-custom-pixel-shader-effect"></a>编译 Direct2D 自定义像素着色器效果

编译包含像素着色器的 Direct2D 自定义效果。 请勿用于顶点或计算自定义效果。

### <a name="multi-processor-compilation"></a>多处理器编译

同时运行多个实例。

## <a name="advanced-property-page"></a>"高级" 属性页

### <a name="suppress-startup-banner"></a>取消显示启动版权标志

取消显示启动版权标志和信息消息。 /nologo

### <a name="treat-warnings-as-errors"></a>将警告视为错误

将所有编译器警告视为错误。 对于新项目，最好在所有编译中使用 /WX；对所有警告进行解析可确保将可能难以发现的代码缺陷减至最少。

## <a name="output-files-property-page"></a>"输出文件" 属性页

### <a name="header-variable-name"></a>标头变量名称

为头文件中的变量名称指定名称 (/Vn [名称])

### <a name="header-file-name"></a>标头文件名

为包含对象代码的头文件指定名称。 (/Fh [名称])

### <a name="object-file-name"></a>对象文件名

为对象文件指定名称。 (/Fo [名称])

### <a name="assembler-output"></a>汇编程序输出

指定汇编语言输出文件的内容。 (/Fc,/Fx)

**方案**

- **无列表**-无列表。
- **仅程序集列表**-程序集代码文件
- **程序集代码和 hex**程序集代码和十六进制列表文件

### <a name="assembler-output-file"></a>汇编程序输出文件

指定程序集代码清单文件的文件名

## <a name="see-also"></a>请参阅

[C++项目属性页引用](property-pages-visual-cpp.md)<br>
[“命令行”属性页](command-line-property-pages.md)<br>
[编译着色器](https://go.microsoft.com/fwlink/p/?LinkID=258284&clcid=0x409)
