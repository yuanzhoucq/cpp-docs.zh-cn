---
title: execution_character_set |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
dev_langs:
- C++
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b6cb84ae6ffebda3dd335bc001463e2d8579f99
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="executioncharacterset"></a>execution_character_set
指定执行字符集，用于字符串和字符文本。 文本标记为 u8 前缀不需要此指令。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma execution_character_set("target")  
```  
  
#### <a name="parameters"></a>参数  
 `target`  
 指定目标执行字符集。 当前唯一的目标执行设置支持为"utf-8"。  
  
## <a name="remarks"></a>备注  
 此编译器指令已废弃不用从 Visual Studio 2015 Update 2 开始。 我们建议你使用 **/execution-charset:utf-8**或 **/utf-8**一起使用的编译器选项`u8`窄字符和字符串文本包含扩展上的前缀字符。 有关详细信息`u8`前缀，请参阅[字符串和字符文本](../cpp/string-and-character-literals-cpp.md)。 有关编译器选项的详细信息，请参阅[/execution-charset （设置执行字符集）](../build/reference/execution-charset-set-execution-character-set.md)和[/utf-8 （设为源和可执行文件字符集 utf-8）](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)。  
  
 `#pragma execution_character_set("utf-8")`指令指示编译器要窄字符和在源代码中的窄字符串文本编码为 utf-8 的可执行文件中。 此输出编码是独立于所使用的源文件编码。  
  
 默认情况下，编译器将窄字符和窄字符串编码为执行字符集中使用的当前代码页。 这意味着，Unicode 或 DBCS 字符在文字之外的当前代码页范围都转换为输出中的默认值替换字符。 Unicode 和 DBCS 字符被截断为其低序位字节。 这是几乎可以肯定并非您的预期。 你可以指定 utf-8 编码文本的源文件中通过使用`u8`前缀。 编译器将这些 utf-8 编码的字符串传递给保持不变的输出。 通过使用 u8 前缀的窄字符文本必须为一个字节，适合或截断输出。  
  
 默认情况下，Visual Studio 作为源字符集，用于解释输出的源代码中使用的当前代码页。 当在读入文件时，Visual Studio 将其解释根据当前的代码页设置的文件代码页，除非或者文件的开头时检测到了一个字节顺序标记 (BOM) 或 UTF 16 个字符。 由于 utf-8 无法设置与当前代码页中，当自动检测遇到源文件编码为 utf-8 无 BOM，Visual Studio 将假定它们通过使用当前代码页进行编码。 源文件中的字符，超出范围的指定或自动检测到代码页可能会导致编译器警告和错误。  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/execution-charset （设置执行字符集）](../build/reference/execution-charset-set-execution-character-set.md)   
 [/utf-8（将源和可执行字符集设置为 UTF-8）](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)