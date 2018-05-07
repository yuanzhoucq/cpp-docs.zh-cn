---
title: XDCMake 参考 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- xdcmake
dev_langs:
- C++
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 383347dc5cd1ce0dcadff6bdee802b90fd52e85d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="xdcmake-reference"></a>XDCMake 参考
xdcmake.exe 是一个程序，将.xdc 文件编译为一个.xml 文件。 如果使用编译的源代码，创建.xdc 文件由 Visual c + + 编译器为每个源代码文件[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)和源代码文件时包含带有 XML 标记的文档注释。  
  
### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中使用 xdcmake.exe  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。  
  
2.  打开**配置属性**文件夹。  
  
3.  单击**XML 文档注释**属性页。  
  
> [!NOTE]
>  在命令行的 xdcmake.exe 选项与选项不同，在开发环境 （属性页） 中使用 xdcmake.exe 时。 有关在开发环境中使用 xdcmake.exe 的信息，请参阅[XML 文档生成器工具属性页](../ide/xml-document-generator-tool-property-pages.md)。  
  
## <a name="syntax"></a>语法  
 xdcmake `input_filename options`  
  
## <a name="parameters"></a>参数  
 其中：  
  
 `input_filename`  
 用于输入到 xdcmake.exe.xdc 文件的文件名称。 指定一个或多个.xdc 文件或使用 *.xdc 若要使用当前目录中的所有.xdc 文件。  
  
 `options`  
 零个或多个以下：  
  
|选项|描述|  
|------------|-----------------|  
|/？，/帮助|显示有关 xdcmake.exe 帮助。|  
|/assembly:*filename*|允许您指定的值\<程序集 > 标记的.xml 文件中。  默认情况下，值\<程序集 > 标记等同于.xml 文件的文件名。|  
|/nologo|禁止显示版权消息。|  
|/out:*filename*|允许您指定的.xml 文件的名称。  默认情况下，.xml 文件的名称是由 xdcmake.exe 处理的第一个.xdc 文件的文件名。|  
  
## <a name="remarks"></a>备注  
 生成项目时，visual Studio 将自动调用 xdcmake.exe。 你也可以调用 xdcmake.exe 在命令行。  
  
 请参阅[建议的文档注释标记](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)有关将文档注释添加到源代码文件的详细信息。  
  
## <a name="see-also"></a>请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)