---
title: -源-charset （集源字符集） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- source-charset
- /source-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4f010eb0f0b83dbc41ebeff624033e59d582535
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="source-charset-set-source-character-set"></a>/source-charset （设置源字符集）
允许您指定可执行文件的源字符集。  
  
## <a name="syntax"></a>语法  
  
```  
/source-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>自变量  
 **IANA_name**  
 IANA 定义字符集名称。  
  
 **CPID**  
 为十进制数的代码页标识符。  
  
## <a name="remarks"></a>备注  
 你可以使用 **/source-charset**选项以指定扩展的源字符设置为使用你的源文件包括基本源字符集中未表示的字符时。 源字符集是程序的用于你的源文本解释为用作输入在编译之前先预处理阶段内部表示形式的编码。 然后，内部表示形式将转换为执行字符集在可执行文件中存储字符串和字符值。 你可以使用任一 IANA 或 ISO 的字符集名称，或句点 （.） 后跟以指定要使用的字符集的 3 到 5 数字十进制代码页标识符。 支持代码页标识符的列表和字符集名称，请参阅[代码页标识符](http://msdn.microsoft.com/library/windows/desktop/dd317756)。  
  
 默认情况下，Visual Studio 会检测以确定源是否该文件在编码的 Unicode 格式，例如 utf-16 或 utf-8 字节顺序标记。 如果不找到任何字节顺序标记，则它假定源文件使用编码的当前的用户代码页，除非你指定一个字符名称或代码页的设置方式使用 **/source-charset**选项。 Visual Studio 允许你使用任何几个字符编码保存你的 c + + 源代码。 有关源和执行字符集的详细信息，请参阅[字符集](../../cpp/character-sets.md)语言文档中。  
  
 你提供的源字符集必须映射到字符集，相同的代码点的 7 位 ASCII 字符或多个编译错误是有可能遵循。 你的源字符集还必须是可映射到扩展设置 utf-8 编码的 Unicode 字符。 不是采用 utf-8 编码的字符表示通过特定于实现的替代。 Microsoft 编译器使用的这些字符的问号。  
  
 如果你想要设置的源字符集和执行字符集为 utf-8，则可以使用 **/utf-8**作为快捷方式的编译器选项。 它等效于指定 **/源-charset:utf-8 /execution-charset:utf-8**命令行上。 所有这些选项还允许 **/validate-charset**默认情况下的选项。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**， **C/c + +**，**命令行**文件夹。  
  
3.  在**高级选项**，添加 **/source-charset**选项，并指定你的首选编码。  
  
4.  选择**确定**以保存所做的更改。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [/execution-charset （设置执行字符集）](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/utf-8 （设为源和可执行文件字符集为 utf-8）](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate-charset（验证兼容的字符）](../../build/reference/validate-charset-validate-for-compatible-characters.md)