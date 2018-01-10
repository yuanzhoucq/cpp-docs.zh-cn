---
title: "-Zl （省略默认库名） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /zi
- VC.Project.VCCLCompilerTool.OmitDefaultLibName
dev_langs: C++
helpviewer_keywords:
- -Zl compiler option [C++]
- ZI compiler option
- Omit Default Library Name compiler option
- /Zl compiler option [C++]
- default libraries, omitting names
ms.assetid: b27d39d0-44d6-498c-84ae-27c1326fee59
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b77b9c1033be1f6144d92b6051118ca85aaaf20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zl-omit-default-library-name"></a>/Zl（省略默认库名）
省略.obj 文件中的默认 C 运行时库名称。 默认情况下，编译器将库的名称放入 .obj 文件中以将链接器定向到正确的库。  
  
## <a name="syntax"></a>语法  
  
```  
/Zl  
```  
  
## <a name="remarks"></a>备注  
 默认库的详细信息，请参阅[使用运行时库](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
 你可以使用**/Zl**来编译你打算放入库的.obj 文件。 虽然省略库名称节省仅少量空间来容纳单个.obj 文件，但总保存为无意义的库，其中包含许多对象模块中。  
  
 此选项是一个高级的选项。 将设置此选项将移除可能要求你的应用程序，从而导致链接时错误，如果你的应用程序依赖于这种支持的某些 C 运行时库支持。 如果使用此选项必须提供所需的组件以某种其他方式。  
  
 使用[/NODEFAULTLIB （忽略库）](../../build/reference/nodefaultlib-ignore-libraries.md)。 若要指示链接器忽略库引用所有.obj 文件中。  
  
 有关详细信息，请参阅 [ CRT 库功能](../../c-runtime-library/crt-library-features.md)。  
  
 使用编译时**/Zl**，`_VC_NODEFAULTLIB`定义。  例如:  
  
```  
// vc_nodefaultlib.cpp  
// compile with: /Zl  
void Test() {  
   #ifdef _VC_NODEFAULTLIB  
      int i;  
   #endif  
  
   int i;   // C2086  
}  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**高级**属性页。  
  
4.  修改**省略默认库名**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitDefaultLibName%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)