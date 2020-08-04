---
title: 不完整类型
ms.date: 11/04/2016
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
ms.openlocfilehash: 192a6556fd8a5d3039598b883ed7c870fc01ad12
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229644"
---
# <a name="incomplete-types"></a>不完整类型

不完整类型  是一种用于描述标识符但缺少确定该标识符的大小所需的信息的类型。 “不完整类型”可以是：

- 您尚未指定其成员的结构类型。

- 您尚未指定其成员的联合类型。

- 您尚未指定其维度的数组类型。

`void` 类型是无法完成的不完整类型。 若要完成不完整类型，请指定缺少的信息。 以下示例演示如何创建和完成不完整类型。

- 若要创建不完整的结构类型，请声明结构类型而不指定其成员。 在本例中，`ps` 指针指向称为 `student` 的不完整的结构类型。

    ```C
    struct student *ps;
    ```

- 若要完成不完整的结构类型，请在稍后在指定其成员的同一范围中声明相同的结构类型，如下所示：

    ```C
    struct student
    {
        int num;
    }                   /* student structure now completed */
    ```

- 若要创建不完整的数组类型，请声明数组类型而不指定其重复计数。 例如：

    ```C
    char a[];  /* a has incomplete type */
    ```

- 若要完成不完整的数组类型，请在稍后在指定其重复计数的同一范围中声明相同的名称，如下所示：

    ```C
    char a[25]; /* a now has complete type */
    ```

## <a name="see-also"></a>请参阅

[声明和类型](../c-language/declarations-and-types.md)
