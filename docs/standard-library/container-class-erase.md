---
title: Container Class::erase | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 368b722f03a68445ddd016705aa8bebc6f33e6f5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842607"
---
# <a name="container-classerase"></a>Container Class::erase

> [!NOTE]
> 本主题位于 Visual C++ 文档内，作为在 C++ 标准库内使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

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

第一个成员函数删除指向的受控序列的元素 *_Where*。 第二个成员函数将移除范围 [`first`、`last`) 中的受控序列的元素。 两者都返回一个迭代器，指定已移除的任何元素之外保留的第一个元素或 [end](../standard-library/container-class-end.md)（若此类元素不存在）。

成员函数仅在复制操作引发异常时才引发异常。

## <a name="see-also"></a>请参阅

[Sample Container 类](../standard-library/sample-container-class.md)<br/>
