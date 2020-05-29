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
ms.openlocfilehash: 087cd613fa0dfd9cb6e07ac47a6a38d63bba004e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167870"
---
# <a name="resource-files-c"></a>资源文件 (C++)

> [!NOTE]
> 由于 .NET 编程语言中的项目不使用资源脚本文件，因此必须从**解决方案资源管理器**打开资源。 使用[图像编辑器](../windows/image-editor-for-icons.md)和[二进制编辑器](binary-editor.md)处理托管项目中的资源文件。
>
> 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

术语 "*资源文件*" 可以指多个文件类型，例如：

- 程序的资源脚本 (.rc) 文件。

- 资源模板 (.rct) 文件。

- 作为独立文件存在的单个资源。 此类型包括在 .rc 文件中引用的位图、图标或光标文件。

- 开发环境生成的标头文件。 此类型包括从 .rc 文件中引用 `Resource.h`。

在其他文件类型（如 .exe、.dll 和 .res 文件）中找到的资源称为*资源*。

您可以使用项目中的*资源文件*和*资源*。 你还可以处理不是当前项目的一部分或在 Visual Studio 开发环境外部创建的项目。 例如，你能够：

- 使用嵌套的条件包含资源文件。

- 更新现有资源或将其转换为C++视觉对象。

- 从当前资源文件中导入图形资源或向其导出图形资源。

- 包含不能由开发环境修改的共享或只读标识符（符号）。

- 在可执行（.exe）文件中包括不需要编辑（或不应编辑）的资源，例如多个项目之间共享的资源。

- 包含开发环境不支持的资源类型。

有关资源的详细信息，请参阅如何[创建资源](../windows/how-to-create-a-resource-script-file.md)、[管理资源](../windows/how-to-copy-resources.md)和[在编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。

## <a name="editable-resources"></a>可编辑资源

可以打开以下类型的文件来编辑它们所包含的资源：

| 文件名 | 说明 |
|---|---|
| .rc | 资源脚本文件 |
| .rct | 资源模板文件 |
| .res | 资源文件 |
| .resx | 托管资源文件 |
| .exe | 可执行文件 |
| .dll | 动态链接库文件 |
| .bmp、.ico、.dib、。 | 位图、图标、工具栏和光标文件 |

编辑资源时，Visual Studio 环境适用于并影响以下文件：

| 文件名 | 说明 |
|---|---|
| Resource.h | 开发环境生成的包含符号定义的标头文件。<br/><br/>在源代码管理中包含此文件。 |
| Filename.aps | 用于快速加载的当前资源脚本文件的二进制版本。<br /><br /> 资源编辑器不会直接读取 .rc 或 resource .h 文件。 资源编译器将它们编译为资源编辑器使用的 ap 文件。 该文件是一个编译步骤，只存储符号数据。<br/><br/>对于普通的编译过程，在编译过程中不会丢弃符号（如注释）以外的信息。<br/><br/>每当 ap 文件与 .rc 文件不同步时，就会重新生成 .rc 文件。 例如，在**保存**时，资源编辑器会覆盖 .rc 文件和资源 .h 文件。 对资源本身所做的任何更改都将保留在 .rc 文件中，但在覆盖 .rc 文件后，注释将始终会丢失。 有关如何保留注释的信息，请参阅[在编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。<br/><br/>通常，不应在源代码管理中包含 ap 文件。 |
| .rc | 包含当前项目中的资源脚本的资源脚本文件。 每当进行保存时，.aps 文件就会覆盖此文件。<br/><br/>在源代码管理中包含此文件。 |

## <a name="manifest-resources"></a>清单资源

在C++桌面项目中，清单资源是描述应用程序所使用的依赖项的 XML 文件。 例如，在 Visual Studio 中，此 MFC 向导生成的清单文件定义应用程序应使用的 Windows 公共控件 Dll 的版本：

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

对于 Windows XP 或 Windows Vista 应用程序，清单资源应指定应用程序要使用的最新版本的 Windows 公共控件。 上面的示例使用版本 `6.0.0.0`，该版本支持[Syslink 控件](/windows/win32/Controls/syslink-overview)。

> [!NOTE]
> 每个模块只能有一个清单资源。

若要查看清单资源中包含的版本和类型信息，请在 XML 查看器或 Visual Studio 文本编辑器中打开该文件。 如果从 [资源视图](../windows/resource-view-window.md)打开清单资源，则资源将以二进制格式打开。

### <a name="to-open-a-manifest-resource"></a>打开清单资源

1. 在 Visual Studio 中打开项目，然后导航到**解决方案资源管理器**。

1. 展开 "**资源文件**" 文件夹，然后：

   - 若要在文本编辑器中打开，请双击 *.manifest*文件。

   - 若要在另一个编辑器中打开，请右键单击 *.manifest*文件，然后选择 "**打开方式**"。 指定要使用的编辑器，然后选择 "**打开**"。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>另请参阅

[使用资源文件](../windows/working-with-resource-files.md)<br/>
[资源标识符（符号）](../windows/symbols-resource-identifiers.md)<br/>
[资源编辑器](../windows/resource-editors.md)<br/>
