---
title: '-FU (命名强制 #using 文件) |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs:
- C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a92e8d30d2c15ac07bc5a6ff3e6438da46438674
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597496"
---
# <a name="fu-name-forced-using-file"></a>/FU（命名强制 #using 文件）
可以使用作为传递到的文件名称的替代方法的编译器选项[#using 指令](../../preprocessor/hash-using-directive-cpp.md)源代码中。  
  
## <a name="syntax"></a>语法  
  
```  
/FU file  
```  
  
## <a name="arguments"></a>自变量  
 `file`  
 指定要在此编译中引用的元数据文件。  
  
## <a name="remarks"></a>备注  
 /FU 开关只采用一个文件名。 若要指定多个文件，请对每个文件使用 /FU。  
  
 如果使用的 C + + /cli CLI 并引用要使用元数据[友元程序集](../../dotnet/friend-assemblies-cpp.md)功能，不能使用 **/FU**。 您必须将 `#using` 与 `[as friend]` 特性一起使用，才能在代码中引用元数据。 友元程序集不支持在 Visual c + + 组件扩展 C + + /cli CX。  
  
 有关如何创建程序集或模块的公共语言运行时 (CLR) 的信息，请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。 了解如何构建在 C + + /CX 中，请参阅[构建应用程序和库](../../cppcx/building-apps-and-libraries-c-cx.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +** 文件夹。  
  
3.  选择**高级**属性页。  
  
4.  修改**强制 #using**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>。  
  
## <a name="see-also"></a>请参阅  
 [输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)