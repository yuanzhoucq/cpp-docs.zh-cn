---
title: Container Class::rend | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rend method
ms.assetid: 80f3dd04-dd2c-4b52-b0ed-d567ec5d186c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cf4e963d4afcdfdf3c4ba18347e06489392e5db
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="container-classrend"></a>Container Class::rend

> [!NOTE]
> 本主题位于 Visual C++ 文档内，作为在 C++ 标准库内使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

该成员函数返回一个反向访问迭代器，指向序列的第一个元素（或刚超出空序列末尾的位置）并指定反向序列的末尾。

## <a name="syntax"></a>语法

```

    const_reverse_iterator rend() const;


reverse_iterator rend();
```

## <a name="see-also"></a>请参阅

[Sample Container 类](../standard-library/sample-container-class.md)<br/>
