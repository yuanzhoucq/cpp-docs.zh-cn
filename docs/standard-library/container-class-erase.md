---
title: Container Class::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 0ef4db1c14942fc896f10095ff2331648d27c820
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221639"
---
# <a name="container-classerase"></a>Container Class::erase

> [!NOTE]
> 本主题是在 microsoftC++作为容器中使用的非功能性示例文档C++标准库。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

删除元素。

## <a name="syntax"></a>语法

```

    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>备注

第一个成员函数删除由指向受控序列的元素 *_Where*。 第二个成员函数将移除范围 [`first`、`last`) 中的受控序列的元素。 两者都返回一个迭代器，指定已移除的任何元素之外保留的第一个元素或 [end](../standard-library/container-class-end.md)（若此类元素不存在）。

成员函数仅在复制操作引发异常时才引发异常。

## <a name="see-also"></a>请参阅

[Sample Container 类](../standard-library/sample-container-class.md)<br/>
