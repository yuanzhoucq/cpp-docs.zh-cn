---
title: allocate
ms.date: 11/04/2016
f1_keywords:
- allocate_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
ms.openlocfilehash: 0bf31423cd76c838cbeffa7458bbccb89592bf43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227616"
---
# <a name="allocate"></a>allocate

**Microsoft 专用**

**`allocate`** 声明说明符命名要在其中分配数据项的数据段。

## <a name="syntax"></a>语法

> **`__declspec(allocate("`***segname* **`))`***声明符*

## <a name="remarks"></a>备注

必须使用以下杂注之一声明名称*segname* ：

- [code_seg](../preprocessor/code-seg.md)

- [const_seg](../preprocessor/const-seg.md)

- [data_seg](../preprocessor/data-seg.md)

- [init_seg](../preprocessor/init-seg.md)

- [区](../preprocessor/section.md)

## <a name="example"></a>示例

```cpp
// allocate.cpp
#pragma section("mycode", read)
__declspec(allocate("mycode"))  int i = 0;

int main() {
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[`__declspec`](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)
