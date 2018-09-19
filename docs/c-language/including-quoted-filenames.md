---
title: 包含用引号引起来的文件名 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3e865df95d92dcad6b414da11677b5212e9a9f3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109933"
---
# <a name="including-quoted-filenames"></a>包含用引号引起来的文件名

**ANSI 3.8.2** 对可包含的源文件的带引号名称的支持

如果在两组双引号 (" ") 之间为包含文件指定完整明确的路径说明，则预处理器只搜索该路径说明并会忽略标准目录。

对于指定为 [#include](../preprocessor/hash-include-directive-c-cpp.md)“path-spec”的包含文件，目录搜索从父文件的目录开始，然后在任何祖父级文件的目录中继续进行。 因此，搜索将相对于包含当前正在处理的源文件的目录开始。 如果没有祖父文件且未找到该文件，则搜索会像文件名括在尖括号中一样继续进行。

## <a name="see-also"></a>请参阅

[预处理指令](../c-language/preprocessing-directives.md)