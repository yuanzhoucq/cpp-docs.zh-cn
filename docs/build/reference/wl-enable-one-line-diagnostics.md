---
title: -WL （启用单行诊断） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /wl
dev_langs:
- C++
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 48ba6ab05ac596c98c4fa5a95971735c62267a35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL（启用单行诊断）
将其他信息追加到错误或警告消息。  
  
## <a name="syntax"></a>语法  
  
```  
/WL  
```  
  
## <a name="remarks"></a>备注  
 错误和警告消息，从 c + + 编译器可以跟出现时，默认情况下，新行上的其他信息。 从命令行编译时，可以将信息的其他行追加到错误或警告消息。 当捕获你的生成输出到日志文件，然后处理该日志以查找所有错误和警告，这可能有必要。 与其他行，分号将区分开来的错误或警告消息。  
  
 并非所有错误和警告消息都具有附加行的信息。 下面的代码将生成信息; 其他行的错误它将允许你测试的效果，当你使用**/WL**。  
  
```  
// compiler_option_WL.cpp  
// compile with: /WL  
#include <queue>  
int main() {  
   std::queue<int> q;  
   q.fromthecontinuum();   // C2039  
}  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)