---
title: 创建项目 (ATL 教程，第 1 部分) |Microsoft 文档
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1aedf7b4112d4c8d4bb5b2a174e93925f5a46ce5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>创建项目（ATL 教程，第 1 部分）
本教程将指导你逐步完成创建用于显示多边形 ActiveX 对象的非特性化 ATL 项目。 对象包括允许用户的选项，若要更改组成的多边形和代码以刷新显示的边数。  
  
> [!NOTE]
>  ATL 和 MFC 不通常支持 Visual Studio Express 版本。  
  
> [!NOTE]
>  本教程将创建与多边形的示例相同的源代码。 如果你想要避免手动输入的源代码，您可以下载它从[多边形示例抽象](../visual-cpp-samples.md)。 在你完成本教程中，或将其用于自己的项目中的错误检查，然后可以引用多边形源代码。  
  
### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>若要创建使用 ATL 项目向导的初始 ATL 项目  
  
1.  在 Visual Studio 开发环境中，单击**新建**上**文件**菜单，，然后单击**项目**。  
  
2.  单击**Visual c + + 项目**文件夹，然后选择**ATL 项目**。  
  
3.  类型`Polygon`作为项目名称。  
  
     源代码的位置通常将默认为 My Documents\Visual Studio 项目中，并将自动创建一个新文件夹。  
  
4.  单击**确定**和 ATL 项目向导将打开。  
  
5.  单击**应用程序设置**若要查看可用的选项。  
  
6.  在创建控件和控件必须为进程内服务器时，将保留**应用程序类型**为 DLL。  
  
7.  在其默认值，保留其他选项，然后单击**完成**。  
  
 ATL 项目向导将通过生成多个文件创建项目。 通过展开多边形对象，可以在解决方案资源管理器中查看这些文件。 下面列出了这些文件。  
  
|文件|描述|  
|----------|-----------------|  
|Polygon.cpp|包含的实现`DllMain`， `DllCanUnloadNow`， `DllGetClassObject`， `DllRegisterServer`，和`DllUnregisterServer`。 此外包含在对象映射，这是你的项目中的 ATL 对象的列表。 这是初始值为空值。|  
|Polygon.def|此模块定义文件提供有关所需的 DLL 导出的信息链接器。|  
|Polygon.idl|接口定义语言文件，其中介绍了特定于你的对象的接口。|  
|Polygon.rgs|此注册表脚本包含注册程序的 DLL 的信息。|  
|Polygon.rc|资源文件，其中最初包含版本信息和包含的项目名称的字符串。|  
|Resource.h|资源文件的标头文件。|  
|Polygonps.def|此模块定义文件提供有关支持跨单元调用导出所需的代理和存根代码的信息链接器。|  
|stdafx.cpp|将文件`#include`ATL 实现文件。|  
|stdafx.h|将文件`#include`ATL 标头文件。|  
  
1.  在解决方案资源管理器，右键单击`Polygon`项目。  
  
2.  在快捷菜单上，单击**属性**。  
  
3.  单击**链接器**。 更改**每 UserRedirection**选项设为**是**。  
  
4.  单击 **“确定”**。  
  
 在下一步的步骤中，你将在你的项目中添加控件。  
  
 [步骤 2 到](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## <a name="see-also"></a>请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)

