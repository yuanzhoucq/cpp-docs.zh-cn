---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c3a04f68b7fd17b2b6459c219a98fd99ec2d62d4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397253"
---
# <a name="local-masm"></a>LOCAL (MASM)

在第一个指令中，在宏内，**本地**定义宏的每个实例特有的标签。

## <a name="syntax"></a>语法

> **本地** *localname* ⟦， *localname* .。。⟧
>
> **本地***标签*⟦ __\[__ *count* __]__ ⟧⟦ __：__ *type*⟧⟦ __，__ *label* ⟦ __\[__ *count* __]__ *⟧⟦⟧* ⟧

## <a name="remarks"></a>备注

在第二个指令中，在过程定义（**PROC**）内，**本地**创建在过程中存在的基于堆栈的变量。 *标签*可以是简单变量，也可以是包含*count*元素的数组。

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)
