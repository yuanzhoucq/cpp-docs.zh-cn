---
title: "-FC （诊断中源代码文件的完整路径） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
dev_langs: C++
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b055b5431d41bc09fbdd2750c01d3efca8f21287
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC（所诊断源代码文件的完整路径）

使编译器显示传递给编译器在诊断中源代码文件的完整路径。

## <a name="syntax"></a>语法

> /FC

## <a name="remarks"></a>备注

请考虑下面的代码示例：

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

而无需**/FC**，诊断的文本将类似于此诊断的文本：

- compiler_option_FC.cpp(5)： 错误 C2143： 语法错误： 缺少; 之前}

与**/FC**，诊断的文本将类似于此诊断的文本：

- c:\test\compiler_option_FC.cpp(5)： 错误 C2143： 语法错误： 缺少; 之前}

**/FC**也需要如果你想要使用时，请参阅文件名称的完整路径 （& a) #95; &#95;文件 &#95; &#95;宏。  请参阅[预定义的宏](../../preprocessor/predefined-macros.md)有关的详细信息 &#95; &#95;文件 &#95; &#95;。

**/FC**选项也将暗示**/ZI**。 有关详细信息**/ZI**，请参阅[/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开**配置属性**节点。

1. 展开**C/c + +**节点。

1. 选择**高级**属性页。

1. 修改**使用完整路径**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)   
[设置编译器选项](../../build/reference/setting-compiler-options.md)