---
title: -utf-8 （设为源和可执行文件字符集 utf-8） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- /utf-8
dev_langs:
- C++
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90520cd9ad4af484714306c37567ab041a826fcc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377483"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/utf-8 （设为源和可执行文件字符集为 utf-8）
指定两个源字符集和执行字符集为 utf-8。  
  
## <a name="syntax"></a>语法  
  
```  
/utf-8  
```  
  
## <a name="remarks"></a>备注  
 你可以使用 **/utf-8**选项以指定的源和执行字符集作为通过使用 utf-8 编码。 它等效于指定 **/源-charset:utf-8 /execution-charset:utf-8**命令行上。 所有这些选项还允许 **/validate-charset**默认情况下的选项。 支持代码页标识符的列表和字符集名称，请参阅[代码页标识符](http://msdn.microsoft.com/library/windows/desktop/dd317756)。  
  
 默认情况下，Visual Studio 会检测以确定源是否该文件在编码的 Unicode 格式，例如 utf-16 或 utf-8 字节顺序标记。 如果不找到任何字节顺序标记，则它假定源文件使用编码的当前的用户代码页，除非使用指定代码页 **/utf-8**或 **/source-charset**选项。 Visual Studio 允许你使用任何几个字符编码保存你的 c + + 源代码。 有关源和执行字符集的信息，请参阅[字符集](../../cpp/character-sets.md)语言文档中。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**， **C/c + +**，**命令行**文件夹。  
  
3.  在**高级选项**，添加 **/utf-8**选项，并指定你的首选编码。  
  
4.  选择**确定**以保存所做的更改。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [/execution-charset （设置执行字符集）](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/source-charset （设置源字符集）](../../build/reference/source-charset-set-source-character-set.md)   
 [/validate-charset（验证兼容的字符）](../../build/reference/validate-charset-validate-for-compatible-characters.md)