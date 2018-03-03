---
title: "-DLL （生成 DLL） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /dll
dev_langs:
- C++
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28a501590e127e5f27a465366611b4dbf3be175c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dll-build-a-dll"></a>/DLL（生成 DLL）
```  
/DLL  
```  
  
## <a name="remarks"></a>备注  
 /DLL 选项生成的主输出文件的 DLL。 DLL 通常包含可由其他程序的导出。 有三种方法，用于指定导出，建议使用的顺序依次列出：  
  
1.  [__declspec （dllexport)](../../cpp/dllexport-dllimport.md)的源代码中  
  
2.  [导出](../../build/reference/exports.md)在.def 文件语句  
  
3.  [/导出](../../build/reference/export-exports-a-function.md)LINK 命令中的规范  
  
 程序可以使用多个方法。  
  
 若要生成 DLL 的另一个方法是使用**库**模块定义语句。 /BASE 和 /DLL 选项一起构成了等效于**库**语句。  
  
 未指定此选项在开发环境中;此选项仅供仅在命令行上使用。 使用应用程序向导创建 DLL 项目时，设置此选项。  
  
 请注意，是否创建.dll 之前，可以在初步步骤中，创建你导入的库，你必须传递同一套对象文件时，生成.dll 为通过生成导入库时。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**配置属性**文件夹。  
  
3.  单击**常规**属性页。  
  
4.  修改**配置类型**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)