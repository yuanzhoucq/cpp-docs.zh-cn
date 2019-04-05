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
ms.openlocfilehash: 45db6d0139cfa3aa8a2eaa8fe6d18158cb6646ce
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029390"
---
# <a name="resource-files-c"></a>资源文件 (C++)

> [!NOTE]
> 由于.NET 编程语言中的项目不使用资源脚本文件，则必须打开你的资源**解决方案资源管理器**。 使用[的图像编辑器](../windows/image-editor-for-icons.md)并[二进制编辑器](binary-editor.md)来处理托管项目中的资源文件。
>
> 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

术语*资源文件*多种文件类型，可以参考类似：

- 程序的资源脚本 (.rc) 文件。

- 资源模板 (.rct) 文件。

- 为独立的文件的各个资源。 这种类型包括从.rc 文件引用的位图、 图标或光标文件。

- 由开发环境生成的标头文件。 这种类型包括`Resource.h`，引用从.rc 文件。

在其他文件类型中找到资源如.exe、.dll 和.res 文件被称为*资源*。

您可以使用*资源文件*并*资源*从你的项目中。 您还可以使用那些不属于当前项目或 Visual Studio 在开发环境外部创建。 例如，你可以：

- 使用嵌套的条件包含资源文件。

- 更新现有资源或将它们转换为 Visual c + +。

- 从当前资源文件中导入图形资源或向其导出图形资源。

- 包含不能由开发环境修改的共享或只读标识符（符号）。

- 你不需要编辑 （或不应进行编辑），例如多个项目之间共享资源的可执行文件 (.exe) 文件中包括的资源。

- 包含开发环境不支持的资源类型。

有关资源的详细信息，请参阅如何[创建资源](../windows/how-to-create-a-resource-script-file.md)，[管理的资源](../windows/how-to-copy-resources.md)，并[编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。

## <a name="editable-resources"></a>可编辑资源

以下类型的文件可以打开以便编辑及其包含的资源：

| 文件名 | 描述 |
|---|---|
| .rc | 资源脚本文件 |
| .rct | 资源模板文件 |
| .res | 资源文件 |
| .resx | 托管的资源文件 |
| .exe | 可执行文件 |
| .dll | 动态链接库文件 |
| .bmp, .ico, .dib, .cur | 位图、 图标、 工具栏和光标文件 |

在编辑资源时，Visual Studio 环境处理，并且会影响以下文件：

| 文件名 | 描述 |
|---|---|
| Resource.h | 包含符号定义的开发环境生成的标头文件。<br/><br/>在源代码管理中包括此文件。 |
| Filename.aps | 用于快速加载的当前资源脚本文件的二进制版本。<br /><br /> 资源编辑器不直接读取.rc 或 resource.h 文件。 资源编译器会将其编译为通过资源编辑器使用的.aps 文件中。 该文件是一个编译步骤，只存储符号数据。<br/><br/>与普通编译过程，因为不是符号，如注释的信息将在编译过程中被放弃。<br/><br/>每当.aps 文件与.rc 文件同步时，将重新生成.rc 文件。 例如，当您**保存**，资源编辑器将覆盖.rc 文件和 resource.h 文件。 对资源本身的任何更改依然包含在.rc 文件中，但一旦覆盖.rc 文件就总会丢失注释。 有关如何保留注释的信息，请参阅[编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)。<br/><br/>通常情况下，您不应在源代码管理中包含的.aps 文件。 |
| .rc | 包含当前项目中的资源脚本的资源脚本文件。 每当进行保存时，.aps 文件就会覆盖此文件。<br/><br/>在源代码管理中包括此文件。 |

## <a name="manifest-resources"></a>清单资源

在 c + + 桌面项目中，清单资源是描述应用程序使用的依赖项的 XML 文件。 例如，在 Visual Studio 中此 MFC 向导生成的清单文件定义应用程序应使用哪个版本的 Windows 公共控件 Dll:

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

对于 Windows XP 或 Windows Vista 的应用程序，清单资源应指定要使用的应用程序的 Windows 公共控件的最新版本。 上面的示例使用版本`6.0.0.0`，它也支持[Syslink 控件](/windows/desktop/Controls/syslink-overview)。

> [!NOTE]
> 每个模块只能有一个清单资源。

若要查看的版本和类型包含在清单资源的信息，请在 XML 查看器或 Visual Studio 文本编辑器中打开文件。 如果从 [资源视图](../windows/resource-view-window.md)打开清单资源，则资源将以二进制格式打开。

### <a name="to-open-a-manifest-resource"></a>若要打开清单资源

1. 在 Visual Studio 中打开你的项目，并导航到**解决方案资源管理器**。

1. 展开**资源文件**文件夹，然后：

   - 若要在文本编辑器中打开，双击 *.manifest*文件。

   - 若要打开另一个编辑器中，右键单击 *.manifest*文件，然后选择**打开**。 指定要使用和选择的编辑器**打开**。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[使用资源文件](../windows/working-with-resource-files.md)<br/>
[资源标识符 （符号）](../windows/symbols-resource-identifiers.md)<br/>
[资源编辑器](../windows/resource-editors.md)<br/>