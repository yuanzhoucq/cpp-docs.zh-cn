---
title: 一旦 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.once
- once_CPP
dev_langs:
- C++
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b0e0b2b3667d4a33709caa643e4d26ed70b2990
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912922"
---
# <a name="once"></a>once
指定该文件在编译源代码文件时仅由编译器包含（打开）一次。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma once  
  
```  
  
## <a name="remarks"></a>备注  
 由于编译器将不会在翻译单元中的文件的第一个 #include 后打开和读取文件，因此，使用 `#pragma once` 可减少生成次数。 这称为*多次包括优化*。 它具有类似的效果 *#include 防护*惯用语法，后者使用预处理器宏定义来避免多次包含文件的内容。 这也有助于防止违反*单一定义规则*-要求所有模板、 类型、 函数和对象不能超过一个定义在中的代码。  
  
 例如：  
  
```  
// header.h  
#pragma once  
// Code placed here is included only once per translation unit  
  
```  
  
 建议对新代码使用 `#pragma once` 指令，因为它不会用预处理器符号污染全局命名空间。 它需要的键入较少，因此不太会让人分心，并且不会导致符号冲突（不同的头文件使用相同的预处理器符号作为防护值时导致的错误）。 它不属于 C++ 标准，而是由几个常见的编译器移植实现。  
  
 在同一文件中同时使用 #include 防护惯用语法和 `#pragma once` 没有任何优势。 编译器会识别 #include 防护惯用语法，并在标准形式的惯用语法前后未出现任何非注释代码或预处理器指令时实现多次包括优化，实现方法与`#pragma once` 指令相同：  
  
```  
// header.h  
// Demonstration of the #include guard idiom.  
// Note that the defined symbol can be arbitrary.  
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_  
#define HEADER_H_  
// Code placed here is included only once per translation unit  
#endif // HEADER_H_  
  
```  
  
 代码必须可移植到未实现 `#pragma once` 指令的编译器时，建议使用 #include 防护惯用语法以保持与现有代码的一致性，或者建议在不可进行多次包含优化时使用该惯用语法。 在复杂的项目中，当文件系统别名化或使用别名的包括路径使编译器无法按规范路径识别相同的包括文件时可能出现这种情况。  
  
 请注意不要在将多次包括的头文件中使用 `#pragma once` 或 #include 防护惯用语法，这些头文件使用预处理器符号来控制其效果。 这种设计的示例，请参阅\<.h > 标头文件。 此外，还要注意管理包括路径，以避免创建多个指向包括的文件的路径，这会让使用 #include 防护和 `#pragma once` 的多次包括优化无效。  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)