---
title: "Visual c + + 工具和 Visual Studio 版本中的功能 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- versions [C++]
- Visual C++, versions
- editions [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
caps.latest.revision: "51"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 37f1eed2287c8fe655a124b1f76f48a203ab1607
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="visual-c-tools-and-features-in-visual-studio-editions"></a>Visual c + + 工具和 Visual Studio 版本中的功能
下表显示 Visual Studio 中可用的 Visual C++ 功能。 单元格中的 X 指示功能可用；空单元格指示功能不可用。 括号中的说明指示功能可用，但是受限制。  
  
## <a name="platforms"></a>平台  
  
||||||  
|-|-|-|-|-|  
|平台|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|  
|Windows 桌面||X|X|X|  
|通用 Windows 平台（手机、平板电脑、PC、Xbox、IoT 和 HoloLens）|X||X|X|  
|Windows 应用商店 8.1|||X|X|  
|Windows Phone 8.0|||X|X|  
|Android|||X|X|  
|iOS|||X|X|  
  
## <a name="compilers"></a>编译器  
  
|编译器|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|  
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|32 位 X86 编译器|X|X|X|X|  
|X86_arm 跨平台编译器|X||X|X|  
|64 位 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 编译器|||X|X|  
|X86_ [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 跨平台编译器|X|X|X|X|  
  
## <a name="libraries-and-headers"></a>库和标头  
  
|库或标头|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|  
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|Windows 标头和库以及 CRT 库|(X)|X|X|X|  
|C++ 标准库|X|X|X|X|  
|ATL|||X|X|  
|MFC|||X|X|  
|.NET Framework Class Library — .NET Framework 类库||X|X|X|  
|针对 .NET 的 C++ 支持库||X|X|X|  
|OpenMP|X|X|X|X|  
  
## <a name="project-templates"></a>项目模板  
  
|模板|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|  
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|适用于 UWP、Windows 8.1、Windows Phone 8.0 的 XAML 模板|X||X|X|  
|Direct3D 应用程序|X||X|X|  
|DLL（Windows 应用商店应用）|X||X|X|  
|静态库（Windows 应用商店应用）|X||X|X|  
|Windows 运行时组件|X||X|X|  
|单元测试库（Windows 应用商店应用）|X||X|X|  
|ATL 项目|||X|X|  
|类库 (CLR)||X|X|X|  
|CLR 控制台应用程序||X|X|X|  
|CLR 空项目||X|X|X|  
|自定义向导|||X|X|  
|空项目||X|X|X|  
|生成文件项目||X|X|X|  
|MFC ActiveX 控件|||X|X|  
|MFC 应用程序|||X|X|  
|MFC DLL|||X|X|  
|测试项目|X|X|X|X|  
|Win32 控制台应用程序||X|X|X|  
|Win32 项目||X|X|X|  
  
## <a name="tools"></a>工具  
  
|工具|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|  
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|增量链接器|X|X|X|X|  
|程序维护实用工具 (Nmake.exe)||X|X|X|  
|Lib 生成器 (Lib.exe)|X|X|X|X|  
|Windows 资源编译器 (Rc.exe)|X|X|X|X|  
|Windows Resource to Object Converter (CvtRes.exe)||X|X|X|  
|浏览信息维护实用工具 (BscMake.exe)|X|X|X|X|  
|C++ Name Undecorator (Undname.exe)|X|X|X|X|  
|COFF/PE 转储程序 (Dumpbin.exe)|X|X|X|X|  
|COFF/PE 编辑器 (Editbin.exe)|X|X|X|X|  
|MASM (Ml.exe)|||X|X|  
|Spy++|||X|X|  
|ErrLook|||X|X|  
|AtlTrace|||X|X|  
|Devenv.com|||X|X|  
|推理规则|||X|X|  
|将 VCBuild .vcproj 项目升级到 MSBuild (VCUpgrade.exe)|X|X|X|X|  
|按配置优化|||X|X|  
  
## <a name="debugging-features"></a>调试功能  
  
|调试功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|  
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|本机调试|X|X|X|X|  
|natvis（本机类型可视化）|X|X|X|X|  
|图形调试|X||X|X|  
|托管调试||X|X|X|  
|GPU 使用情况|X||X|X|  
|内存使用率|X||X|X|  
|远程调试|X|X|X|X|  
|SQL 调试|||X|X|  
|静态代码分析|有限|有限|X|X|  
  
## <a name="designers-and-editors"></a>设计器和编辑器  
  
|设计器或编辑器|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|  
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|XAML 设计器|X||X|X|  
|CSS 样式设计器/编辑器|X|X|X|X|  
|HTML 样式设计器/编辑器|X|X|X|X|  
|XML 编辑器|X|X|X|X|  
|源代码编辑器|X|X|X|X|  
|工作效率功能：重构、IntelliSense、C++ 代码格式设置|X|X|X|X|  
|Windows 窗体设计器||X|X|X|  
|数据设计器|||X|X|  
|本机资源编辑器（.rc 文件）|||X|X|  
|资源编辑器|X|X|X|X|  
|模型编辑器|X||X|X|  
|着色器设计器|X||X|X|  
  
## <a name="data-features"></a>数据功能  
  
|数据功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio 高级专业版|Visual Studio Enterprise|  
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|---------------------------|------------------------------|  
|数据设计器|||X|X|X|  
|数据对象|||X|X|X|  
|Web 服务|||X|X|X|  
|服务器资源管理器|||X|X|X|  
  
## <a name="build-and-project-systems"></a>生成和项目系统  
  
|生成或项目功能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|  
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|命令行生成 (msbuild.exe)|X|X|X|X|  
|本机多目标||X|X|X|  
|托管多目标||X|X|X|  
|并行生成|X|X|X|X|  
|生成自定义项|X|X|X|X|  
|属性页扩展性|X|X|X|X|  
  
## <a name="automation-and-extensibility"></a>自动化和扩展性  
  
|自动化和扩展性|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|  
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|  
|扩展性对象模型|||X|X|  
|代码模型|||X|X|  
|项目模型|||X|X|  
|资源编辑器模型|||X|X|  
|向导模型|||X|X|  
|设计器对象模型|||X|X|  
  
## <a name="application-lifecycle-management-tools"></a>Application Lifecycle Management 工具  
  
||||||  
|-|-|-|-|-|  
|工具|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|  
|单元测试（本机框架）|X|X|X|X|  
|单元测试（托管框架）||X|X|X|  
|代码覆盖率||||X|  
|手动测试||||X|  
|探索测试||||X|  
|测试用例管理||||X|  
|代码图和依赖项关系图|||只读|X|  
|代码图调试||||X|  
  
## <a name="see-also"></a>另请参阅  
 [安装 Visual Studio](/visualstudio/install/install-visual-studio)   
 [什么是 Visual Studio 中的新增功能](/visualstudio/ide/whats-new-in-visual-studio)   
 [Visual c + + 项目类型](../ide/visual-cpp-project-types.md)   
 [Visual Database Tools 版本](http://msdn.microsoft.com/en-us/a7689adc-f16b-4cc7-b6fe-39ca0c711161)