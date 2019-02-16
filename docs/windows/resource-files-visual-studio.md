---
title: 资源文件 (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- resources [C++]
- .rc files [C++]
- resource files [C++]
- resource script files [C++]
- resource script files [C++], Win-32 based applications
- resource script files [C++], files updated when editing resources
- resources [C++], types of resource files
- rct files [C++]
- rc files [C++]
- resource files [C++], types of
- .rct files [C++]
- resource script files [C++], unsupported types
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
ms.openlocfilehash: 4d56a62dfa350b3113a28355433130563464c6be
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320531"
---
# <a name="resource-files-c"></a>资源文件 (C++)

> [!NOTE]
> 由于.NET 编程语言中的项目不使用资源脚本文件，则必须打开你的资源**解决方案资源管理器**。 可以使用[的图像编辑器](../windows/image-editor-for-icons.md)并[二进制编辑器](binary-editor.md)来处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

术语“资源文件”可以指多个文件类型，包括：

- 程序的资源脚本 (.rc) 文件。

- 资源模板 (.rct) 文件。

- 作为独立文件存在的各个资源，如从 .rc 文件引用的位图、图标或光标文件。

- 由开发环境生成、通过.rc 文件引用的标头文件，如 Resource.h。

此外在其他文件类型，如.exe、.dll 和.res 文件中找到资源。 您可以使用资源和资源文件从你的项目和那些不属于当前项目中。 此外可以使用 Visual Studio 在开发环境中创建的资源文件。 例如，你可以：

- 使用嵌套的条件包含资源文件。

- 更新现有资源或将它们转换为 Visual C++ 格式。

- 从当前资源文件中导入图形资源或向其导出图形资源。

- 包含不能由开发环境修改的共享或只读标识符（符号）。

- 不需要编辑 （或不应编辑的） 在当前项目，例如多个项目之间共享资源在可执行文件 (.exe) 文件中包括的资源。

- 包含开发环境不支持的资源类型。

本部分介绍了如何：

- [创建资源](../windows/how-to-create-a-resource-script-file.md)

- [管理资源](../windows/how-to-copy-resources.md)

- [在编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)

## <a name="editable-resource-file-types"></a>可编辑的资源文件类型

以下类型的文件可以打开以便编辑及其包含的资源：

|文件名|描述|
|---------|-----------------|
|.rc|资源脚本文件|
|.rct|资源模板文件|
|.res|资源文件|
|.resx|托管的资源文件|
|.exe|可执行文件|
|.dll|动态链接库文件|
|.bmp、.ico、.dib 和 .cur|位图、图标、工具栏和光标文件。|

在 Visual Studio 环境处理，并且会在资源编辑会话期间影响以下文件：

|文件名|描述|
|---------------|-----------------|
|Resource.h|由开发环境生成的头文件；包含符号定义。 （在源代码管理中包括此文件。）|
|Filename.aps|当前资源脚本文件的二进制版本；用于快速加载。<br /><br /> 资源编辑器不直接读取.rc 或 resource.h 文件。 资源编译器将它们编译成由资源编辑器使用的 .aps 文件。 该文件是一个编译步骤，只存储符号数据。 与普通编译过程，因为不是符号 （例如注释） 的信息将在编译过程中被放弃。 每当 .aps 文件与 .rc 文件不同步时，就会重新生成 .rc 文件（例如，当你进行“保存”时，资源编辑器将覆盖 .rc 文件和 resource.h 文件）。 对资源本身所做的任何更改依然包含在 .rc 文件中，但一旦覆盖 .rc 文件就总会丢失注释。 有关如何保留注释的信息，请参阅[编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。 （通常情况下，您不应包括.aps 文件在源代码管理中。）|
|.rc|包含当前项目中的资源脚本的资源脚本文件。 每当进行保存时，.aps 文件就会覆盖此文件。 （在源代码管理中包括此文件。）|

## <a name="manifest-resources"></a>清单资源

在 c + + 桌面项目中，清单资源是描述应用程序使用的依赖项的 XML 文件。 例如，在 Visual Studio 中，MFC 向导生成的清单文件定义应用程序应使用的 Windows 公共控件 DLL 是 5.0 版还是 6.0 版：

```xml
<description>Your app description here</description>
<dependency>
    <dependentAssembly>
        <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="X86"
            publicKeyToken="6595b64144ccf1df"
            language="*"
        />
    </dependentAssembly>
</dependency>
```

对于 Windows XP 或 Windows Vista 的应用程序，清单资源不仅指定应用程序使用的最新版本的 Windows 公共控件，v6.0，如上图中，所示，但它也支持[Syslink 控件](/windows/desktop/Controls/syslink-overview)。

若要查看的版本和类型包含在清单资源的信息，可以在 XML 查看器或 Visual Studio 文本编辑器中打开该文件。 如果从 [资源视图](../windows/resource-view-window.md)打开清单资源，则资源将以二进制格式打开。 若要以可视效果更好的格式查看清单资源的内容，必须打开的资源**解决方案资源管理器**。

### <a name="to-open-a-manifest-resource"></a>若要打开清单资源

1. 在 Visual Studio 中打开项目。

1. 导航到**解决方案资源管理器**展开**资源文件**文件夹。

   - 有关文本编辑器中，双击.manifest 文件。

   - 对于其他编辑器中，右击.manifest 文件，并选择**打开方式...**，然后指定要使用和选择的编辑器**打开**。

> [!NOTE]
> 每个模块只能有一个清单资源。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[使用资源文件](../windows/working-with-resource-files.md)<br/>
[资源标识符 （符号）](../windows/symbols-resource-identifiers.md)<br/>
[资源编辑器](../windows/resource-editors.md)<br/>