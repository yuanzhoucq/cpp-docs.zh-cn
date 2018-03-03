---
title: "-导出 （导出函数） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
dev_langs:
- C++
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2183a67679fc216396d03ac31a5a11db8d011454
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="export-exports-a-function"></a>/EXPORT（导出函数）
```  
/EXPORT:entryname[,@ordinal[,NONAME]][,DATA]  
```  
  
## <a name="remarks"></a>备注  
 使用此选项，你可以从你的程序导出函数，以便其他程序可以调用该函数。 你还可以导出数据。 通常在 DLL 中定义导出。  
  
 *Entryname*是函数或数据项的名称，因为它是用于调用程序。 `ordinal`索引指定到的导出表中的范围 1 到 65535;如果不指定`ordinal`，链接将分配一个。 **NONAME**关键字仅作为是执行序号，导出该函数不带*entryname*。  
  
 **数据**关键字指定导出的项是数据项。 必须使用声明中客户端程序的数据项**extern __declspec （dllimport)**。  
  
 有三种方法，用于导出的定义，建议使用的顺序依次列出：  
  
1.  [__declspec （dllexport)](../../cpp/dllexport-dllimport.md)的源代码中  
  
2.  [导出](../../build/reference/exports.md)在.def 文件语句  
  
3.  LINK 命令中 /EXPORT 规范  
  
 可以在同一个程序使用所有三个方法。 当 LINK 在生成包含导出的程序时，还创建导入库，除非在生成中使用了.exp 文件。  
  
 链接使用修饰形式的标识符。 创建的.obj 文件时，编译器将修饰标识符。 如果*entryname*指定到链接器在其未修饰窗体 （即显示在源代码中） 中，链接尝试与名称匹配。 如果它找不到唯一的匹配项，则链接将发出错误消息。 使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具以获取[修饰名](../../build/reference/decorated-names.md)时需要指定到链接器标识符的形式。  
  
> [!NOTE]
>  未指定 C 标识符声明的修饰的形式`__cdecl`或`__stdcall`。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  该选项键入**其他选项**框。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)