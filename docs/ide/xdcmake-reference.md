---
title: "XDCMake 参考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xdcmake"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "xdcmake 程序"
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# XDCMake 参考
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于是生成 .xdc 文件添加到 .xml 文件的过程。  .xdc 文件。每个源代码文件的 Visual C\+\+ 编译器创建，当源代码编译 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 时，因此，当源代码文件包含文档注释标记使用 XML 标记时。  
  
### 使用用于在 Visual Studio 开发环境  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../misc/how-to-open-project-property-pages.md)。  
  
2.  打开 **配置属性** 文件夹。  
  
3.  单击 **XML 文档注释** 属性页。  
  
> [!NOTE]
>  在命令行上用于选项与选项不同，当用于用于开发环境时 \(属性页\)。  有关使用 xdcmake.exe 的信息在开发环境，请参见 [“XML 文档生成器工具”属性页](../ide/xml-document-generator-tool-property-pages.md)"" 。  
  
## 语法  
 xdcmake `input_filename options`  
  
## 参数  
 其中：  
  
 `input_filename`  
 作为输入使用的 .xdc 文件的文件名传递给 xdcmake.exe。  指定一个或多个 .xdc 文件或使用 \*.xdc 使用任何 .xdc 文件在当前目录。  
  
 `options`  
 零个或多个以下各项：  
  
|选项|描述|  
|--------|--------|  
|\/?，\/help|用于显示的帮助。|  
|\/assembly:*filename*|.xml 文件允许您指定 \<assembly\> 标记的值。  默认情况下，\<assembly\> 标记的值会与 .xml 文件的文件名。|  
|\/nologo|取消显示版权消息。|  
|\/out:*filename*|允许您指定 .xml 文件的名称。  默认情况下，.xml 文件的名称是用于处理的第一个 .xdc 文件的文件名。|  
  
## 备注  
 在生成项目时，Visual Studio 将自动调用 xdcmake.exe。  还可以调用用于在命令行。  
  
 请参见 [文档注释的建议的标记](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) 有关添加文档注释的更多信息到源代码文件。  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)