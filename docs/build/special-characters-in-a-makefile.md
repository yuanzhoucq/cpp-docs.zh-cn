---
title: 生成文件中的特殊字符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ae77e769672dcc88a9dd41c901424c8c8150e6b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709354"
---
# <a name="special-characters-in-a-makefile"></a>生成文件中的特殊字符

若要使用 NMAKE 特殊字符作为文字字符，将它的前面放置插入符号 (^)。 NMAKE 会忽略前加上其他字符的插入符号。 特殊字符包括：

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

插入符号 (^) 中带引号的字符串视为文字插入符号字符。 行末尾的脱字号插入文本换行字符在字符串或宏。

在宏中，反斜杠 (\\) 后接新行的字符被替换为空格。

在命令中，百分号 （%） 是一个文件说明符。 若要表示 %按原义在命令中的，指定代替一个双百分号 （%）。 在其他情况下，NMAKE 单个 %按原义解释，但它始终将一个双精度值 %%作为单个 %。 因此，用于表示文本 %%，指定是三个百分号，%%%，或四个百分号 %%%。

若要为原义字符，在命令中使用美元符号 （$），指定两个美元符号 （$$）。 此外可以在其他情况下使用此方法，^ $ 的工作原理。

## <a name="see-also"></a>请参阅

[生成文件的内容](../build/contents-of-a-makefile.md)