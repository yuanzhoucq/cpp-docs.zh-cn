---
title: "属性页 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.NotAProp.Edit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "生成宏"
  - "宏, 项目文件"
  - "项目属性 [C++], 默认值"
  - "项目属性 [C++], 设置"
  - "项目文件宏"
  - "属性页, 项目设置"
  - "用户定义的宏"
  - "用户定义值"
  - "Visual C++ 项目, 属性"
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 属性页 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过使用属性页，可以指定 Visual Studio 项目的设置。  要打开 Visual Studio 项目的**“属性页”**对话框，请在**“项目”**菜单上单击**“属性”**。  
  
 可以指定项目设置，以便它们应用所有生成配置，也可以为每个生成配置指定不同的项目属性。  例如，你可以为“发布”配置指定某些设置，而为“调试”配置指定其他设置。  
  
 并非所有可用页面都一定会显示在**“属性页”**对话框中。  显示哪些页面取决于项目中的文件类型。  
  
 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
## 默认属性与修改后的属性  
 当你使用**“新建项目”**对话框创建项目时，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 会使用指定的项目模板来初始化项目属性。  因此，可以将模板中的属性值视为该项目类型的默认值。  在其他项目类型中，各属性具有的默认值可能不同。  
  
 如果修改了项目属性值，它将显示为粗体。  可出于以下原因修改项目属性：  
  
-   应用程序向导会更改属性，因为它需要与项目模板中指定值不同的属性值。  
  
-   在**“新建项目”**对话框中指定不同的属性值。  
  
-   在项目属性页上指定不同的属性值。  
  
> [!TIP]
>  要查看 MSBuild 用于生成项目的最终属性值设置，请检查预处理器输出文件，该文件可通过以下命令行生成：**MSBuild \/preprocess:***preprocessor\_output\_filename*opt *project\_filename*opt  
  
## 重置属性  
 查看项目的**“属性页”**对话框并在**“解决方案资源管理器”**中选择项目节点时，对于许多属性，都可以选择**“从父级或项目默认设置继承”**或者以其他方式修改该值。  
  
 查看项目的**“属性页”**对话框并在**“解决方案资源管理器”**中选择文件时，对于许多属性，都可以选择**“从父级或项目默认设置继承”**或者以其他方式修改该值。  但是，如果项目包含许多具有与项目默认值不同的属性值的文件，该项目将花较长时间才能生成。  
  
> [!TIP]
>  要刷新**“属性页”**对话框以便显示最新的选项，请单击**“应用”**。  
  
 大部分项目默认设置为系统（平台）默认设置。  某些项目默认设置是派生自样式表，这些样式表是在该项目的**“常规”**配置属性页的**“项目默认值”**节中更新属性时应用的。  有关详细信息，请参阅[“常规”属性页（项目）](../ide/general-property-page-project.md)。  
  
## 指定用户定义的值  
 必须为特定属性定义值。  用户定义的值可以包含一个或多个字母数字字符或项目文件宏名称。  这些属性中的一些只能接受一个用户定义的值，而其他一些则可以接受以分号分隔多个值的列表。  
  
 要为属性指定一个用户定义的值或者要在属性可以接受多个用户定义的值时指定一个列表，请在属性名称右侧一列中执行以下操作之一：  
  
-   键入值或值列表。  
  
-   单击下拉箭头。  如果**“编辑”**可用，则单击它，然后在文本框中键入值或值列表。  另一种指定列表的方法是：在文本框中键入值，每个值占一行。  在属性页上，值将显示为以分号分隔的列表。  
  
     要将项目文件宏作为一个值插入，请单击**“宏”**，然后双击宏名称。  
  
-   单击下拉箭头。  如果**“浏览”**可用，则单击它，然后选择一个或多个值。  
  
 对于多值属性，当单击属性名称右侧列中的下拉箭头时，**“从父级或项目默认设置继承”**选项是可用的，然后单击**“编辑”**。  默认情况下，该选项处于选中状态。  
  
 请注意，属性页仅显示从另一个级别继承的多值属性在当前级别的设置。  例如，如果在**“解决方案资源管理器”**中选定一个文件，并且选择 C\/C\+\+**“预处理器定义”**属性，则会显示文件级定义，而不显示继承的项目级定义。  要同时查看当前级别的值和继承的值，请单击属性名称右侧一列中的下拉箭头，然后单击**“编辑”**。  如果使用 [Visual C\+\+ 项目模型](http://msdn.microsoft.com/zh-cn/06c1bbd9-4c79-4f97-ad6d-2b1dea8ecd1f)，此行为对于文件和项目上的对象也有效。  也就是说，当你在文件级别查询某个属性的值时，将不会获取该属性在项目级别的值。  你必须显式获取该属性在项目级别的值。  此外，属性的某些继承值可能来自于无法以编程方式访问的样式表。  
  
## 本节内容  
  
1.  [“添加引用搜索路径”对话框](http://msdn.microsoft.com/zh-cn/4520d80d-aa9f-4d11-b92b-2f64a1fd5cb2)  
  
2.  [“\<项目名\> 属性页”对话框 \-\>“配置属性”\-\>“清单工具”\-\>“高级”](../ide/advanced-manifest-tool.md)  
  
3.  [“命令行”属性页](../ide/command-line-property-pages.md)  
  
4.  [“自定义生成步骤”属性页：常规](../ide/custom-build-step-property-page-general.md)  
  
5.  [添加引用](../ide/adding-references-in-visual-cpp-projects.md)  
  
6.  [“常规”属性页（文件）](../ide/general-property-page-file.md)  
  
7.  [“常规”属性页（项目）](../ide/general-property-page-project.md)  
  
8.  [“\<项目名\> 属性页”对话框 \-\>“配置属性”\-\>“清单工具”\-\>“常规”](../ide/general-manifest-tool-configuration-properties.md)  
  
9. [“HLSL”属性页](../ide/hlsl-property-pages.md)  
  
10. [HLSL 属性页：高级](../ide/hlsl-property-pages-advanced.md)  
  
11. [HLSL 属性页：常规](../ide/hlsl-property-pages-general.md)  
  
12. [HLSL 属性页：输出文件](../ide/hlsl-property-pages-output-files.md)  
  
13. [“\<项目名\> 属性页”对话框 \-\>“配置属性”\-\>“清单工具”\-\>“输入和输出”](../ide/input-and-output-manifest-tool.md)  
  
14. [“\<项目名\> 属性页”对话框 \-\>“配置属性”\-\>“清单工具”\-\>“独立 COM”](../ide/isolated-com-manifest-tool.md)  
  
15. [“链接器”属性页](../ide/linker-property-pages.md)  
  
16. [“托管资源”属性页](../ide/managed-resources-property-page.md)  
  
17. [清单工具属性页](../ide/manifest-tool-property-pages.md)  
  
18. [“MIDL”属性页](../ide/midl-property-pages.md)  
  
19. [MIDL 属性页：高级](../ide/midl-property-pages-advanced.md)  
  
20. [MIDL 属性页：常规](../ide/midl-property-pages-general.md)  
  
21. [MIDL 属性页：输出](../ide/midl-property-pages-output.md)  
  
22. [“Nmake”属性页](../ide/nmake-property-page.md)  
  
23. [“资源”属性页](../ide/resources-property-pages.md)  
  
24. [“VC\+\+ 目录”属性页](../ide/vcpp-directories-property-page.md)  
  
25. [“Web 引用”属性页](../ide/web-references-property-page.md)  
  
26. [“XML 数据生成器工具”属性页](../ide/xml-data-generator-tool-property-page.md)  
  
27. [“XML 文档生成器工具”属性页](../ide/xml-document-generator-tool-property-pages.md)  
  
## 请参阅  
 [如何：创建和移除项目依赖项](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)   
 [如何：创建和编辑配置](../Topic/How%20to:%20Create%20and%20Edit%20Configurations.md)   
 [部署应用程序](http://msdn.microsoft.com/zh-cn/4ff8881d-0daf-47e7-bfe7-774c625031b4)