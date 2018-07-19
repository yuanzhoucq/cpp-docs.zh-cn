---
title: 资源文件 (Visual Studio) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio]
- .rc files
- resource files
- resource script files
- resource script files, Win-32 based applications
- resource script files, files updated when editing resources
- resources [Visual Studio], types of resource files
- rct files
- resources [C++]
- rc files
- resource files, types of
- .rct files
- resource script files, unsupported types
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b4b56d1f329aee29c37b15590729074d305f04d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879869"
---
# <a name="resource-files-visual-studio"></a>资源文件 (Visual Studio)
> [!NOTE]
>  本材料适用于 Windows 桌面应用程序。 有关通用 Windows 平台应用中的资源的信息，请参阅[定义应用资源](http://msdn.microsoft.com/en-us/476ea844-632c-4467-9ce3-966be1350dd4)。  
>   
> 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
>  
> 由于.NET 编程语言中的项目不使用资源脚本文件，则必须打开您的资源不**解决方案资源管理器**。 你可以使用[图像编辑器](../windows/image-editor-for-icons.md)和[二进制编辑器](binary-editor.md)处理的托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。  
  
 术语“资源文件”可以指多个文件类型，包括：  
  
-   程序的资源脚本 (.rc) 文件。  
  
-   资源模板 (.rct) 文件。  
  
-   作为独立文件存在的各个资源，如从 .rc 文件引用的位图、图标或光标文件。  
  
-   由开发环境生成、通过.rc 文件引用的标头文件，如 Resource.h。  
  
 也可发现 [其他文件类型](../windows/editable-file-types-for-resources.md) 的资源，如 .exe、.dll 和.res 文件。 可以处理项目中的资源和资源文件以及不是当前项目的一部分的资源和资源文件。 还可以处理不是在 Visual Studio 开发环境中创建的资源文件。 例如，你可以：  
  
-   使用嵌套的条件包含资源文件。  
  
-   更新现有资源或将它们转换为 Visual C++ 格式。  
  
-   从当前资源文件中导入图形资源或向其导出图形资源。  
  
-   包含不能由开发环境修改的共享或只读标识符（符号）。  
  
-   在不需要在当前项目过程中进行编辑（或不想进行编辑）的可执行 (.exe) 文件中包含资源，例如多个项目之间共享的资源。  
  
-   包含开发环境不支持的资源类型。  
  
 本节介绍：  
  
-   [创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)  
  
-   [创建新资源](../windows/how-to-create-a-resource.md)  
  
-   [查找资源脚本文件中的资源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
  
-   [以文本格式打开资源脚本文件](../windows/how-to-open-a-resource-script-file-in-text-format.md)  
  
-   [在编译时包含资源](../windows/how-to-include-resources-at-compile-time.md)  
  
-   [复制资源](../windows/how-to-copy-resources.md)  
  
-   [使用资源模板 (.rct)](../windows/how-to-use-resource-templates.md)  
  
-   [导入和导出资源](../windows/how-to-import-and-export-resources.md)  
  
-   [资源的可编辑文件类型](../windows/editable-file-types-for-resources.md)  
  
-   [受资源编辑影响的文件](../windows/files-affected-by-resource-editing.md)  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [资源编辑器](../windows/resource-editors.md)   
 [使用资源文件](../windows/working-with-resource-files.md)   
 [菜单和其他资源](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)

