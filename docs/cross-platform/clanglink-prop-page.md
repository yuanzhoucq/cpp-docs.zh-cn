---
title: Clang 链接器属性 (Android C++)
ms.date: 10/23/2017
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
f1_keywords:
- VC.Project.VCLinkerTool.Clang.OutputFile
- VC.Project.VCLinkerTool.Clang.Soname
- VC.Project.VCLinkerTool.Clang.ShowProgress
- VC.Project.VCLinkerTool.Clang.Version
- VC.Project.VCLinkerTool.Clang.VerboseOutput
- VC.Project.VCLinkerTool.Clang.IncrementalLink
- VC.Project.VCLinkerTool.Clang.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.Clang.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.Clang.UnresolvedReferences
- VC.Project.VCLinkerTool.Clang.OptimizeForMemory
- VC.Project.VCLinkerTool.Clang.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.Clang.ForceSymbolReferences
- VC.Project.VCLinkerTool.Clang.ForceFileOutput
- VC.Project.VCLinkerTool.Clang.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.Clang.GenerateMapFile
- VC.Project.VCLinkerTool.Clang.Relocation
- VC.Project.VCLinkerTool.Clang.FunctionBinding
- VC.Project.VCLinkerTool.Clang.NoExecStackRequired
- VC.Project.VCLinkerTool.Clang.WholeArchive
- VC.Project.VCLinkerTool.Clang.AdditionalOptionsPage
- VC.Project.VCLinkerTool.Clang.AdditionalDependencies
- VC.Project.VCLinkerTool.Clang.LibraryDependencies
ms.openlocfilehash: 55b944040157d13741b992f4ec66c35d1b117d95
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79470249"
---
# <a name="clang-linker-properties-android-c"></a>Clang 链接器属性 (Android C++)

| properties | 说明 | 选项 |
|--|--|--|
| 输出文件 | 该选项可重写链接器创建的程序的默认名称和位置。 (-o) |
| 显示进度 | 打印链接器进度消息。 |
| 版本 | -version 选项让链接器将版本号置于可执行文件的标头中。 |
| 启用详细输出 | -verbose 选项通知链接器输出调试的详细消息。 |
| 启用增量链接 | 此选项通知链接器启用增量链接。 |
| 共享库搜索路径 | 允许用户填入共享库搜索路径。 |
| 附加库目录 | 允许用户重写环境库路径。 （-L 文件夹）。 |
| 报告未解析的符号引用 | 启用后，此选项将报告未解析的符号引用。 |
| 优化内存使用率 | 如有必要，通过重读符号表优化内存使用率。 |
| 忽略特定默认库 | 指定一个或多个要忽略的默认库的名称。 |
| 强制符号引用 | 强制将符号作为未定义符号输入到输入文件中。 |
| 调试器符号信息 | 输出文件中的调试程序符号信息。 | 全部包含<br /><br />忽略不需要的符号以进行重定位处理<br /><br />仅忽略调试器符号信息<br /><br />忽略所有符号信息 |
| 打包调试器符号信息 | 在打包之前剥离调试器符号信息。  使用原始二进制文件的副本进行调试。 |
| 映射文件名 | “映射”选项通知链接器使用用户指定的名称创建映射文件。 |
| 重定位之后将变量标记为只读 | 此选项在重定位之后将变量标记为只读。 |
| 启用即时函数绑定 | 此选项标记用于即时函数绑定的对象。 |
| 需要可执行堆栈 | 此选项将输出标记为不需要可执行堆栈。 |
| 整个存档 | 整个存档使用来自源和其他依赖项的所有代码。 |
| 其他选项 | 附加选项。 |
| 附加依赖项 | 指定要添加到链接命令行的附加项。 |
| 库依赖项 | 此选项可指定要添加到链接器命令行的附加库。 其他库添加到链接器命令行的末尾，后者以*lib*开头 *，以* *结尾。*  (-lFILE) |
