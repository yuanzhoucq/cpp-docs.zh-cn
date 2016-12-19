---
title: "警告: 不能将项目 &quot;project&quot; 中的依赖项 &quot;file&quot; 复制到运行目录，因为它将覆盖引用 &quot;file&quot;。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.copy_version_warning"
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 警告: 不能将项目 &quot;project&quot; 中的依赖项 &quot;file&quot; 复制到运行目录，因为它将覆盖引用 &quot;file&quot;。
依赖项之间有冲突；为使应用程序运行，应将多个具有相同名称的不同程序集文件复制到 bin 目录中。 由于其中一个依赖项是主引用，因此运行目录能够解决该冲突。  
  
 双击该任务列表项会将你带到正发生冲突的主引用节点。  
  
 当发生依赖项冲突，但是已经通过将其中一个冲突依赖项添加为引用而解决此冲突时，出现该警告。 或者，你可能已具有版本 1 引用，然后再添加第二个引用，该引用本身又引用第一个引用的版本 2。  
  
 也就是说，此错误的发生是因为解决方案中的项目之间相互引用，但这些引用被创建为文件引用（使用“添加引用”对话框中的“浏览”按钮），而不是项目到项目的引用（使用“添加引用”对话框上的“项目”选项卡）。 项目到项目的引用的好处在于，它在生成系统中创建了项目之间的依赖项，因而如果从上次生成引用项目之后依赖项目发生了更改，就将生成该依赖项目。 文件引用则不创建生成依赖项，因此有可能生成了引用项目而没有生成依赖项目，于是引用会变得过时；一个项目能引用该项目以前生成的版本。 这可能导致 bin 目录中所需的单个 DLL 同时存在多个版本，而这种情况实际是不可能出现的，因此就会出现此错误消息。  
  
 每当在 bin 目录中出现冲突并且应用程序不能正确工作时，就出现此消息。 即使解决了此问题，该警告仍然会出现，因为项目系统不能确定依赖项的版本是否能与所有组件一起正确工作。  
  
 **更正此错误**  
  
-   将一个（或零个）程序集文件复制到 bin 目录中，这可以通过将这些程序集文件放置于全局程序集缓存中来实现。 全局程序集缓存将解决文件名冲突问题。 由于公共语言运行时知道如何查找全局程序集缓存中的程序集，因此将不会生成程序集文件的本地副本。 有关详细信息，请参阅[使用程序集和全局程序集缓存](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md)和[错误：不能将项目“project”中的依赖项“file”复制到运行目录，因为它将与依赖项“file”冲突](../misc/error-the-dependency-file-in-project-project-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-file.md)。  
  
## 请参阅  
 [管理项目中的引用](../Topic/Managing%20references%20in%20a%20project.md)   
 [全局程序集缓存](../Topic/Global%20Assembly%20Cache.md)   
 [如何：创建和移除项目依赖项](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)