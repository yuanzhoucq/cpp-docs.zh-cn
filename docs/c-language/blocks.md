---
title: Blocks
ms.date: 11/04/2016
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
ms.openlocfilehash: 4f308864e6e85f74e40d9c9df200a0254fea366a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325905"
---
# <a name="blocks"></a>Blocks

包含在大括号 ({ }  ) 中的声明、定义和语句的序列称为“块”。 C 中有两种类型的块。由一个或多个语句构成的语句“复合语句”（请参阅[复合语句](../c-language/compound-statement-c.md)）是一种类型的块。 另一种类型的块是“函数定义”，它由一个复合语句（函数的主体）和函数的关联的“标头”（函数名称、返回类型和形参）构成。 一个块位于其他块中的情况称作“嵌套”。

请注意，当所有复合语句包含在大括号内时，并非大括号内的所有内容都构成复合语句。 例如，虽然数组、结构或枚举元素的说明可出现在大括号内，但它们不是复合语句。

## <a name="see-also"></a>请参阅

[源文件和源程序](../c-language/source-files-and-source-programs.md)
