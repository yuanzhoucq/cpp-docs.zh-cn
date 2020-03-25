---
title: __if_not_exists 语句
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 7372ac127a7b4dd5c05d58cfecca25f87690b0ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178168"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists 语句

**__If_not_exists**语句测试指定的标识符是否存在。 如果该标识符不存在，则执行指定的语句块。

## <a name="syntax"></a>语法

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*identifier*|要测试其存在性的标识符。|
|*前瞻性*|如果*标识符*不存在，要执行的一个或多个语句。|

## <a name="remarks"></a>备注

> [!CAUTION]
>  若要获得最可靠的结果，请在以下约束下使用 **__if_not_exists**语句。

- 将 **__if_not_exists**语句仅应用于简单类型，而不是模板。

- 将 **__if_not_exists**语句应用于类的内部或外部的标识符。 不要将 **__if_not_exists**语句应用于局部变量。

- 仅在函数体中使用 **__if_not_exists**语句。 在函数体的外部， **__if_not_exists**语句只能测试完全定义的类型。

- 在测试重载函数时，不能测试特定形式的重载。

**__If_not_exists**语句的补集是[__if_exists](../cpp/if-exists-statement.md)语句。

## <a name="example"></a>示例

有关如何使用 **__if_not_exists**的示例，请参阅[__if_exists 语句](../cpp/if-exists-statement.md)。

## <a name="see-also"></a>另请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[__if_exists 语句](../cpp/if-exists-statement.md)
