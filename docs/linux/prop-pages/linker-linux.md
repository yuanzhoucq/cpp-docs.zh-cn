---
title: "链接器属性 (Linux C++) | Microsoft Docs"
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.LibraryDependencies
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
ms.openlocfilehash: 963d73e73e42930f0245c0fef443da27bf451bc6
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="linker-properties-linux-c"></a>链接器属性 (Linux C++)

## <a name="general"></a>常规
属性 | 描述 | 选项
--- | ---| ---
输出文件 | 该选项可重写链接器创建的程序的默认名称和位置。 (-o)
显示进度 | 打印链接器进度消息。
版本 | -version 选项让链接器将版本号置于可执行文件的标头中。
启用详细输出 | -verbose 选项通知链接器输出调试的详细消息。
跟踪 | --trace 选项通知链接器输出被处理的输入文件。
跟踪符号 | 打印显示有符号的文件列表。 (--trace-symbol=symbol)
打印映射 | --print-map 选项通知链接器输出链接映射。
报告未解析的符号引用 | 启用此选项将报告未解析的符号引用。
优化内存使用率 | 如有必要，通过重读符号表优化内存使用率。
共享库搜索路径 | 允许用户填入共享库搜索路径。 (-rpath-link=path)
附加库目录 | 允许用户重写环境库路径。 （-L 文件夹）。
链接器 | 指定链接期间要调用的程序，或远程系统上链接器的路径。
链接超时 | 远程链接超时（毫秒）。
复制输出 | 指定是否要将生成输出文件从远程系统复制到本地计算机。

## <a name="input"></a>输入
属性 | 描述 | 选项
--- | ---| ---
忽略特定默认库 | 指定一个或多个要忽略的默认库的名称。 （--exclude-libs lib、lib）
忽略默认库 | 忽略默认库，仅搜索明确指定的库。
强制取消定义符号引用 | 强制将符号作为未定义符号输入到输入文件中。 (-u symbol --undefined=symbol)
库依赖项 | 此选项可指定要添加到链接器命令行的附加库。 会将其他库添加到前缀为“lib”和结尾扩展名为“.a”的链接器命令行的末尾。  (-lFILE)
附加依赖项 | 指定要添加到链接命令行的附加项。

## <a name="debugging"></a>调试
属性 | 描述 | 选项
--- | ---| ---
调试程序符号信息 | 输出文件中的调试程序符号信息。 | 全部包含<br>仅忽略调试程序符号信息<br>忽略所有符号信息<br>
映射文件名 | “映射”选项通知链接器使用用户指定的名称创建映射文件。 (-Map=)

## <a name="advanced"></a>高级
属性 | 描述 | 选项
--- | ---| ---
重定位之后将变量标记为只读 | 此选项在重定位之后将变量标记为只读。
启用即时函数绑定 | 此选项标记用于即时函数绑定的对象。
不需要可执行堆栈 | 此选项将输出标记为不需要可执行堆栈。
整个存档 | 整个存档使用来自源和其他依赖项的所有代码。


## <a name="additional-options"></a>附加选项



