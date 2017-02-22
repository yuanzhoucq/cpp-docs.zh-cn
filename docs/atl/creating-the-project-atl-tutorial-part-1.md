---
title: "创建项目（ATL 教程，第 1 部分） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 创建项目（ATL 教程，第 1 部分）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本教程通过创建 ActiveX 对象公开多边形的一个非 ATL 项目布局的过程。  对象包括允许用户的选项卡更改组成多边形和代码的边数刷新显示。  
  
> [!NOTE]
>  ATL 和 MFC 在 Visual Studio 学习版通常不受支持。  
  
> [!NOTE]
>  本教程中创建源代码和 POLYGON 示例相同。  如果要避免手动输入源代码，可以下载它从 [POLYGON 示例摘要](../top/visual-cpp-samples.md)。  然后可以引用多边形源代码，当您通过本教程中工作，或使用它检查您的项目的错误。  
  
### 使用 ATL 项目向导，若要创建初始 ATL 项目  
  
1.  在 Visual Studio 开发环境中，在 **文件** 菜单中单击 **新建**，然后单击 **项目**。  
  
2.  单击 **Visual C\+\+ 项目** 文件夹并选择 **ATL 项目**。  
  
3.  键入 `Polygon` 作为项目名称。  
  
     源代码的位置通常将默认为" my documents\\Visual Studio 项目，因此，一个新文件夹将自动创建。  
  
4.  单击 **确定** 和 ATL 项目向导"打开。  
  
5.  单击查看选项的 **应用程序设置** 可用。  
  
6.  当您创建控件，因此，控件必须是进程内服务器，保留 **应用程序类型** 作为 DLL。  
  
7.  保留其他选项在默认值，然后单击 **完成**。  
  
 ATL 项目向导将生成多个文件创建项目。  通过展开多边形对象查看在解决方案资源管理器中这些文件。  文件下面列出。  
  
|文件|描述|  
|--------|--------|  
|Polygon.cpp|包含 `DllMain`、`DllCanUnloadNow`、`DllGetClassObject`、`DllRegisterServer`和 `DllUnregisterServer`的实现。  它包含对象映射，是 ATL 对象列表在项目中。  这最初为空。|  
|Polygon.def|此模块定义文件提供链接器提供有关您的 DLL 需要的导出的信息。|  
|Polygon.idl|接口定义语言 \(idl\) 文件，描述接口特定于您的对象。|  
|Polygon.rgs|此注册表脚本包含注册的程序的 DLL 信息。|  
|Polygon.rc|资源文件，最初包含项目名称的版本信息和一个字符串。|  
|Resource.h|资源文件的头文件。|  
|Polygonps.def|此模块定义文件提供链接器提供有关该代理需要的导出的信息，并的存根 \(stub\) 代码跨单元的支持调用。|  
|stdafx.cpp|将 `#include` ATL 实现文件中的文件。|  
|stdafx.h|将 `#include` ATL 标头文件的文件。|  
  
1.  在解决方案资源管理器中，右击 `Polygon` 项目。  
  
2.  在快捷菜单上，单击 **属性**。  
  
3.  单击 **链接器**。  更改 **每用户重定向** 选项为。  
  
4.  单击**“确定”**。  
  
 在下一步，您将添加一个控件添加到项目中。  
  
 [在到步骤 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## 请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)