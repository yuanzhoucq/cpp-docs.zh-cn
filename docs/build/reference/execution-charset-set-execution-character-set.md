---
title: "-执行-charset （集执行字符集） |Microsoft 文档"
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
- execution-charset
- /execution-charset
dev_langs: C++
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cfb315c0dece0edc6228f70ed3900be80543cc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="execution-charset-set-execution-character-set"></a>/execution-charset （设置执行字符集）
允许您指定可执行文件的执行字符集。  
  
## <a name="syntax"></a>语法  
  
```  
/execution-charset:[IANA_name|.CPID]  
```  
  
## <a name="arguments"></a>自变量  
 **IANA_name**  
 IANA 定义字符集名称。  
  
 **CPID**  
 代码页标识符。  
  
## <a name="remarks"></a>备注  
 你可以使用**/execution-charset**选项以指定执行字符集。 执行字符集是用于输入到所有预处理步骤在编译阶段你程序的文本的编码。 此字符集用于编译的代码的任何字符串或字符文本的内部表示。 设置此选项以指定要在你的源文件包括基本执行字符集中可表示的字符时使用的扩展的执行字符集。 你可以使用任一 IANA 或 ISO 的字符集名称，或句点 （.） 后跟以指定要使用的字符集的 3 到 5 数字十进制代码页标识符。 支持代码页标识符的列表和字符集名称，请参阅[代码页标识符](http://msdn.microsoft.com/library/windows/desktop/dd317756)。  
  
 默认情况下，Visual Studio 会检测以确定源是否该文件在编码的 Unicode 格式，例如 utf-16 或 utf-8 字节顺序标记。 如果不找到任何字节顺序标记，则它假定源文件使用编码的当前的用户代码页，除非你指定一个字符名称或代码页的设置方式使用**/source-charset**选项或**/utf-8**选项。 Visual Studio 允许你使用任何几个字符编码保存你的 c + + 源代码。 有关源和执行字符集的信息，请参阅[字符集](../../cpp/character-sets2.md)语言文档中。  
  
 如果你想要设置的源字符集和执行字符集为 utf-8，则可以使用**/utf-8**作为快捷方式的编译器选项。 它等效于指定**/源-charset:utf-8 /execution-charset:utf-8**命令行上。 所有这些选项还允许**/validate-charset**默认情况下的选项。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**， **C/c + +**，**命令行**文件夹。  
  
3.  在**高级选项**，添加**/execution-charset**选项，并指定你的首选编码。  
  
4.  选择**确定**以保存所做的更改。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [/source-charset （设置源字符集）](../../build/reference/source-charset-set-source-character-set.md)   
 [/utf-8 （设为源和可执行文件字符集为 utf-8）](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)   
 [/validate-charset （验证兼容字符）](../../build/reference/validate-charset-validate-for-compatible-characters.md)