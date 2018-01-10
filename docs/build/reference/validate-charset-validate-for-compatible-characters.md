---
title: "-验证-charset （验证兼容字符） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /validate-charset
- validate-charset
dev_langs: C++
helpviewer_keywords: /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7694eb94fe1b50d1892dab399b523a5b0e6deef7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/validate-charset （验证兼容字符）
验证源文件文本包含字符仅可表示为 utf-8。  
  
## <a name="syntax"></a>语法  
  
```  
/validate-charset[-]  
```  
  
## <a name="remarks"></a>备注  
 你可以使用**/validate-charset**选项来验证源的代码包含仅可以表示源字符集中的字符的设置和执行字符集。 当你指定自动启用此检查**/source-charset**， **/execution-charset**，或**/utf-8**编译器选项。 你可以通过指定显式禁用此检查**/ 验证-charset-**选项。  
  
 默认情况下，Visual Studio 会检测以确定源是否该文件在编码的 Unicode 格式，例如 utf-16 或 utf-8 字节顺序标记。 如果不找到任何字节顺序标记，则它假定源文件使用编码的当前的用户代码页，除非使用指定代码页**/utf-8**或**/source-charset**选项。 Visual Studio 允许你使用任何几个字符编码保存你的 c + + 源代码。 有关源和执行字符集的信息，请参阅[字符集](../../cpp/character-sets2.md)语言文档中。 支持代码页标识符的列表和字符集名称，请参阅[代码页标识符](http://msdn.microsoft.com/library/windows/desktop/dd317756)。  
  
 Visual Studio 使用的源字符集和执行字符集之间的转换的过程的内部字符编码为 utf-8。 如果不能执行字符集中表示的源文件中的字符，utf-8 转换将替换一个问号？ 字符。 **/Validate-charset**选项导致编译报告一个警告，如果发生这种情况。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**， **C/c + +**，**命令行**文件夹。  
  
3.  在**高级选项**，添加**/validate-charset**选项，并指定你的首选编码。  
  
4.  选择**确定**以保存所做的更改。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [/execution-charset （设置执行字符集）](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/source-charset （设置源字符集）](../../build/reference/source-charset-set-source-character-set.md)   
 [/utf-8 （设为源和可执行文件字符集为 utf-8）](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)