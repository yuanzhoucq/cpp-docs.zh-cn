---
title: "/MANIFEST（创建并行程序集清单） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.GenerateManifest"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFEST 链接器选项"
  - "MANIFEST 链接器选项"
  - "-MANIFEST 链接器选项"
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# /MANIFEST（创建并行程序集清单）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MANIFEST[:{EMBED[,ID=#]|NO}]  
```  
  
## 备注  
 \/MANIFEST 指定链接器应创建并行清单文件。  有关清单文件的更多信息，请参见[清单文件参考](http://msdn.microsoft.com/library/aa375632)。  
  
 默认为 \/MANIFEST。  
  
 \/MANIFEST:EMBED 选项指定链接器应当将该图像作为RT\_MANIFEST类型资源嵌入清单文件。  选项 `ID`参数是使用的资源的ID清单。  使用1表示可执行文件。  使用2表示DDl启用指定专用依赖项。  如果 `ID` 参数未被指定，如果\/DLL 选项被设置，则默认值为 2；否则，默认值为 1。  
  
 从 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 开始，可执行文件的清单文件包含用于指定用户帐户控制 \(UAC\) 信息的节。  如果指定 \/MANIFEST 但未指定 [\/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md) 和 [\/DLL](../../build/reference/dll-build-a-dll.md)，则将默认 UAC 片段插入到 UAC 清单中并将 UAC 级别设置为 *asInvoker*。  有关 UAC 级别的更多信息，请参见 [\/MANIFESTUAC（将 UAC 信息嵌入到清单中）](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)。  
  
 若要更改 UAC 的默认行为，请执行下列操作之一：  
  
-   指定 \/MANIFESTUAC 选项并将 UAC 级别设置为所需的值。  
  
-   如果不想在清单中生成 UAC 片段，或指定 \/MANIFESTUAC:NO 选项。  
  
 如果未指定 \/MANIFEST，但指定了 [\/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md) 注释，则创建清单文件。  如果指定了 \/MANIFEST:NO，则将不会创建清单文件。  
  
 如果指定 \/MANIFEST，则清单文件的名称与输出文件的名称相同，并且会在文件名后追加 .manifest。  例如，如果输出文件名是 MyFile.exe，则清单文件名是 MyFile.exe.manifest。如果指定 \/MANIFESTFILE:*name*，则清单的名称将是您在 *name*中指定的名称。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“清单文件”**属性页。  
  
5.  修改**“生成清单”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)