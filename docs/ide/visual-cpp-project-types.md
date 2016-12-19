---
title: "Visual C++ 项目类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "程序 [C++], 项目"
  - "项目模板 [Visual Studio], C++"
  - "TODO 注释 [C++]"
  - "项目 [C++], 类型"
  - "模板 [C++], 项目"
  - "应用程序 [C++], 项目"
  - "Visual C++ 项目, 类型"
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual C++ 项目类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用项目模板来创建基本程序结构、菜单、工具栏、图标、引用以及适合要创建的项目类型的 `#include` 语句。 Visual Studio 包括多种类型的 Visual C\+\+ 项目模板并为其中许多项目模板提供了向导，以便可以在创建项目时对其进行自定义。 在创建项目之后，可以立即生成它并运行应用程序；在开发应用程序时最好间歇性生成该项目。  
  
 不必使用模板来创建项目，但在大多数情况下这样做会更为高效，因为修改提供的项目文件和结构比从头创建它们更为简单。  
  
> [!NOTE]
>  你可以使用 C\+\+ 项目模板来创建 C 语言项目。 在生成的项目中，找到文件扩展名为 .cpp 的文件并将它更改为 .c。 然后，在该项目（而非解决方案）的“项目属性”页上，依次展开“配置属性”和“C\/C\+\+”，然后选择“高级”。 将“编译为”设置更改为“编译为 C 代码 \(\/TC\)”。  
  
## 项目模板  
 Visual Studio 包括以下 Visual C\+\+ 项目模板。  
  
### 应用商店应用  
  
||  
|-|  
|[适用于应用商店应用的 C\#、VB 和 C\+\+ 项目模板](http://go.microsoft.com/fwlink/p/?LinkID=262279)|  
  
### ATL  
  
|项目模板|如何创建项目|  
|----------|------------|  
|ATL 项目|[创建 ATL 项目](../atl/reference/creating-an-atl-project.md)|  
  
### CLR  
  
|项目模板|  
|----------|  
|[\(NOTINBUILD\)类库模板 \(C\+\+\)](http://msdn.microsoft.com/zh-cn/0d779bfa-5c5a-4b10-a9d5-a6791764a78f)|  
|[如何：创建 CLR 控制台应用程序](../dotnet/how-to-create-clr-console-applications-cpp-cli.md)|  
|[NOTINBUILD CLR 空项目模板 \(C\+\+\)](http://msdn.microsoft.com/zh-cn/f57c5572-5581-440f-b684-eec646764f08)|  
  
### 常规  
  
|项目模板|如何创建项目|  
|----------|------------|  
|空项目|[创建解决方案和项目](../Topic/Creating%20Solutions%20and%20Projects.md)|  
|自定义向导|[创建自定义向导](../ide/creating-a-custom-wizard.md)|  
|生成文件项目|[创建生成文件项目](../ide/creating-a-makefile-project.md)|  
  
### MFC  
  
|项目模板|如何创建项目|  
|----------|------------|  
|MFC ActiveX 控件|[创建 MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)|  
|MFC 应用程序|[创建 MFC 应用程序](../mfc/reference/creating-an-mfc-application.md)|  
|MFC DLL|[创建 MFC DLL 项目](../mfc/reference/creating-an-mfc-dll-project.md)|  
  
### 测试  
  
|项目模板|如何创建项目|  
|----------|------------|  
|托管测试项目|[创建单元测试项目](../Topic/Create%20a%20unit%20test%20project.md)|  
|本机单元测试项目|[使用测试资源管理器对本机代码进行单元测试](http://msdn.microsoft.com/zh-cn/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
  
### Win32  
  
|项目模板|如何创建项目|  
|----------|------------|  
|Win32 控制台项目|[创建控制台应用程序](../windows/creating-a-console-application.md)|  
|Win32 项目|[如何：创建 Windows 桌面应用程序](../Topic/How%20to:%20Create%20a%20Windows%20Desktop%20Application.md)|  
  
## TODO 注释  
 许多由项目模板生成的文件都包含 TODO 注释，这些注释可帮助你标识提供自己的源代码的位置。 若要深入了解如何添加代码，请参阅[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)和[Working with Resource Files](../mfc/working-with-resource-files.md)。  
  
## 请参阅  
 [使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用项目来创建应用程序](http://msdn.microsoft.com/zh-cn/3339fa90-bac2-4b95-8361-662a2e0e7dfe)   
 [CLR 项目](../ide/files-created-for-clr-projects.md)