---
title: 字符串文本的存储 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d87998f7e9d579c012f5db2f38f20886c1e74c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="storage-of-string-literals"></a>字符串文本的存储
文本字符串的字符将按顺序存储在连续内存位置。 字符串文本中的转义序列（例如，\\\\ 或 \\"）将作为单个字符进行计数。 null 字符（由 \0 转义序列表示）自动追加到每个字符串并标记该字符串的末尾。 （这会在[转换阶段](../preprocessor/phases-of-translation.md) 7 出现。）请注意，编译器无法在两个不同的地址存储两个相同的字符串。 [/GF](../build/reference/gf-eliminate-duplicate-strings.md) 强制编译器将相同字符串的单个副本置于可执行文件中。  
  
## <a name="remarks"></a>备注  
 **Microsoft 专用**  
  
 字符串具有静态存储持续时间。 有关存储持续时间的信息，请参阅[存储类](../c-language/c-storage-classes.md)。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [C 字符串文本](../c-language/c-string-literals.md)