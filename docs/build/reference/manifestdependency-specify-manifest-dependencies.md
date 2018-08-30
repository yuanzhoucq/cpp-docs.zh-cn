---
title: -MANIFESTDEPENDENCY （指定清单依赖项） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
dev_langs:
- C++
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d486047b708e0c3412aa63e0a0b026a2a4204f71
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213894"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY（指定清单依赖项）
```  
/MANIFESTDEPENDENCY:manifest_dependency  
```  
  
## <a name="remarks"></a>备注  
 /MANIFESTDEPENDENCY 允许您指定将放入特性\<依赖项 > 部分中的清单文件。  
  
 请参阅[/MANIFEST （创建并行程序集清单）](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)有关如何创建一个清单文件的信息。  
  
 有关详细信息\<依赖项 > 节的清单文件，请参阅[发行者配置文件](/windows/desktop/SbsCs/publisher-configuration-files)。  
  
 /MANIFESTDEPENDENCY 信息可以传递给链接器在两种方式之一：  
  
-   直接在命令行上 （或响应文件中） 与 /MANIFESTDEPENDENCY。  
  
-   通过[注释](../../preprocessor/comment-c-cpp.md)杂注。  
  
 下面的示例显示了 /MANIFESTDEPENDENCY 注释杂注，通过传递  
  
```  
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")  
```  
  
 这会导致清单文件中的以下条目：  
  
```  
<dependency>  
  <dependentAssembly>  
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />  
  </dependentAssembly>  
</dependency>  
```  
  
 可以在命令行，如下所示传递相同的 /MANIFESTDEPENDENCY 注释：  
  
```  
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"  
```  
  
 链接器将收集 /MANIFESTDEPENDENCY 注释，消除重复项，然后到清单文件添加生成的 XML 字符串。  如果链接器发现有冲突的条目，清单文件将变为已损坏，应用程序将无法启动 （条目可能会添加到事件日志中，指示失败的原因）。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开“配置属性”节点。  
  
3.  展开**链接器**节点。  
  
4.  选择**清单文件**属性页。  
  
5.  修改**附加清单依赖项**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)