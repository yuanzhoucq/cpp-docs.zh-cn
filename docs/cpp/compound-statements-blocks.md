---
title: 复合语句（块）
ms.date: 11/04/2016
f1_keywords:
- '}'
- '{'
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
ms.openlocfilehash: 60d7e88c5ccccac5a1d967a91c8a82dd954d9afc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337343"
---
# <a name="compound-statements-blocks"></a>复合语句（块）

复合语句由以大括号 **（***） 括起来的零个或多个语句组成。 可以在任何期望语句出现的位置使用复合语句。 复合语句通常称为“块”。

## <a name="syntax"></a>语法

```
{ [ statement-list ] }
```

## <a name="remarks"></a>备注

下面的示例使用复合语句作为**if** *语句的语句*部分（有关语法的详细信息，请参阅[if 语句](../cpp/if-else-statement-cpp.md)）：

```cpp
if( Amount > 100 )
{
    cout << "Amount was too large to handle\n";
    Alert();
}
else
{
    Balance -= Amount;
}
```

> [!NOTE]
> 由于声明是语句，因此声明可以是*语句列表中*的语句之一。 因此，复合语句内声明的名称（而不是显式声明为静态的名称）具有局部范围和（对于对象）生存期。 有关使用本地作用域的名称的处理的详细信息，请参阅[Scope。](../cpp/scope-visual-cpp.md)

## <a name="see-also"></a>另请参阅

[C++ 语句概述](../cpp/overview-of-cpp-statements.md)
