---
title: Container Class::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 1fa3fe7dee10f3033b84a671fdc35c193cd6ec3c
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257892"
---
# <a name="container-classerase"></a>Container Class::erase

> [!NOTE]
> 本主题在 Microsoft C++文档中作为在C++标准库中使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

删除元素。

## <a name="syntax"></a>语法

```cpp
iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>备注

第一个成员函数通过 *_Where*删除受控序列的元素。 第二个成员函数将移除范围 [`first`、`last`) 中的受控序列的元素。 两者都返回一个迭代器，指定已移除的任何元素之外保留的第一个元素或 [end](../standard-library/container-class-end.md)（若此类元素不存在）。

成员函数仅在复制操作引发异常时才引发异常。

## <a name="see-also"></a>另请参阅

[Sample Container 类](../standard-library/sample-container-class.md)
