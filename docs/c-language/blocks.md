---
title: 块 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9704b499106fc59364f5cc9ae97277939e835a77
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025317"
---
# <a name="blocks"></a>Blocks

包含在大括号 ({ }) 中的声明、定义和语句的序列称为“块”。 C 中有两种类型的块。由一个或多个语句构成的语句“复合语句”（请参阅[复合语句](../c-language/compound-statement-c.md)）是一种类型的块。 另一种类型的块是“函数定义”，它由一个复合语句（函数的主体）和函数的关联的“标头”（函数名称、返回类型和形参）构成。 一个块位于其他块中的情况称作“嵌套”。

请注意，当所有复合语句包含在大括号内时，并非大括号内的所有内容都构成复合语句。 例如，虽然数组、结构或枚举元素的说明可出现在大括号内，但它们不是复合语句。

## <a name="see-also"></a>请参阅

[源文件和源程序](../c-language/source-files-and-source-programs.md)