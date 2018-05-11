---
title: '&lt;bitset&gt; | Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <bitset>
dev_langs:
- C++
helpviewer_keywords:
- <bitset> header
- bitset header
ms.assetid: af30a9b9-489e-46e3-9d29-5f3ea07ae6dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9294edb0a6b258fff9041c01dc4354e918a8c380
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="ltbitsetgt"></a>&lt;bitset&gt;

定义模板类位组和两个支持模板函数（用于表示和处理固定大小的位序列）。

## <a name="syntax"></a>语法

```

#include <bitset>

```

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator&](../standard-library/bitset-operators.md#op_amp)|执行两个位组间的按位“与”。|
|[operator<\<](../standard-library/bitset-operators.md#op_lt_lt)|将位序列的文本表示形式插入标准输出流中。|
|[operator>>](../standard-library/bitset-operators.md#op_gt_gt)|将位序列的文本表示形式插入标准输入流中。|
|[operator^](../standard-library/bitset-operators.md#op_xor)|执行两个位组间的按位“异或”。|
|[operator&#124;](../standard-library/bitset-operators.md#op_or)|执行两个位组间的按位“或”。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[bitset 类](../standard-library/bitset-class.md)|模板类介绍一种类型的对象，该对象存储由固定数量的位构成的序列，这些位提供一种紧凑方式来保留一组项或条件的标志。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
