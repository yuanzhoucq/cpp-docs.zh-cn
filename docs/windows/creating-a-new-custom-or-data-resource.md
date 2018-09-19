---
title: 创建新的自定义资源或数据资源 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a92e7904b3b42422bebf5a80e0f1b03dd818f86
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314570"
---
# <a name="creating-a-new-custom-or-data-resource-c"></a>创建新的自定义资源或数据资源 （c + +）

可以通过右键单击你的项目中将资源放在单独的文件使用标准资源脚本 (.rc) 文件语法，然后包括该文件创建新的自定义资源或数据资源**解决方案资源管理器**，然后单击**资源包括**快捷菜单上。

### <a name="to-create-a-new-custom-or-data-resource"></a>创建新的自定义资源或数据资源

1. [创建 .rc 文件](../windows/how-to-create-a-resource-script-file.md) （其中包含自定义资源或数据资源）。

   可以在 .rc 文件中键入自定义数据，格式为以 null 结尾的带引号的字符串，或十进制、十六进制或八进制格式的整数。

2. 在“解决方案资源管理器” 中，右键单击项目的 .rc 文件，然后在快捷方式菜单中单击“资源包含”  。

3. 在中**编译时指令**框中，键入`#include`语句，为包含自定义资源的文件的名称。 例如：

```cpp
    #include mydata.rc
 ```

   请确保所键入内容的语法和拼写正确。 在“编译时指令”  框中键入时，其内容会插入到资源脚本文件中。

4. 单击“确定”  以记录所做的更改。

创建自定义资源的另一种方法是将外部文件导入为自定义资源。 有关详细信息，请参阅 [导入和导出资源](../windows/how-to-import-and-export-resources.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[二进制编辑器](binary-editor.md)