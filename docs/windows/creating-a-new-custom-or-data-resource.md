---
title: 创建新的自定义资源或数据资源 |Microsoft 文档
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
- resources [Visual Studio], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c82e41544bde9cdd945e23f4ea5884e4e76ae22b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="creating-a-new-custom-or-data-resource"></a>创建新的自定义资源或数据资源
可以通过以下方式来创建新的自定义资源或数据资源：在使用标准资源脚本 (.rc) 文件语法的独立文件中放置资源，然后在解决方案资源管理器中右键单击项目并单击快捷菜单上的 **资源包含** 来包含文件。  
  
### <a name="to-create-a-new-custom-or-data-resource"></a>创建新的自定义资源或数据资源  
  
1. [创建 .rc 文件](../windows/how-to-create-a-resource-script-file.md) （其中包含自定义资源或数据资源）。  
  
     可以在 .rc 文件中键入自定义数据，格式为以 null 结尾的带引号的字符串，或十进制、十六进制或八进制格式的整数。  
  
2.  在“解决方案资源管理器” 中，右键单击项目的 .rc 文件，然后在快捷方式菜单中单击“资源包含”  。  
  
3.  在“编译时指令”  框中，键入 **#include** 语句，为包含自定义资源的文件命名。 例如：  
  
 ```  
    #include mydata.rc  
 ```  
  
     请确保所键入内容的语法和拼写正确。 在“编译时指令”  框中键入时，其内容会插入到资源脚本文件中。  
  
4.  单击“确定”  以记录所做的更改。  
  
 创建自定义资源的另一种方法是将外部文件导入为自定义资源。 有关详细信息，请参阅 [导入和导出资源](../windows/how-to-import-and-export-resources.md)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [二进制编辑器](binary-editor.md)

