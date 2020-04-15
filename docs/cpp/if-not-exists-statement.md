---
title: __if_not_exists 语句
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 1118f9fcca525b2b2d5869fb507ee974d2b0d28f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374142"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists 语句

**__if_not_exists**语句测试指定的标识符是否存在。 如果该标识符不存在，则执行指定的语句块。

## <a name="syntax"></a>语法

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*标识符*|要测试其存在性的标识符。|
|*语句*|如果*标识符*不存在，要执行的一个或多个语句。|

## <a name="remarks"></a>备注

> [!CAUTION]
> 要获得最可靠的结果，请使用以下约束下的 **__if_not_exists**语句。

- 将 **__if_not_exists**语句仅应用于简单类型，而不是模板。

- 将 **__if_not_exists**语句应用于类内部或外部的标识符。 不要将 **__if_not_exists**语句应用于局部变量。

- 仅在函数正文中使用 **__if_not_exists**语句。 在函数的正文之外 **，__if_not_exists**语句只能测试完全定义的类型。

- 在测试重载函数时，不能测试特定形式的重载。

**__if_not_exists**语句的补充是[__if_exists](../cpp/if-exists-statement.md)语句。

## <a name="example"></a>示例

有关如何使用 **__if_not_exists**的示例，请参阅[__if_exists 语句](../cpp/if-exists-statement.md)。

## <a name="see-also"></a>另请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)<br/>
[__if_exists声明](../cpp/if-exists-statement.md)
