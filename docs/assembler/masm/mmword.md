---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: e4ebaa9d47a569bc9cf7d843d3ddb54ca5d713a0
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328222"
---
# <a name="mmword"></a>MMWORD

用于 64 位多媒体操作数与 MMX 和 SSE (XMM) 说明。

## <a name="syntax"></a>语法

> MMWORD

## <a name="remarks"></a>备注

`MMWORD` 是一种。  在添加到 MASM MMWORD 之前, 的等效功能可能达到使用：

```asm
    mov mm0, qword ptr [ebx]
```

虽然这两个说明适用于 64 位操作数`QWORD`是 64 位无符号整数的类型和`MMWORD`是 64 位多媒体值的类型。

`MMWORD` 用于表示与相同的类型[__m64](../../cpp/m64.md)。

## <a name="example"></a>示例

```asm
    movq     mm0, mmword ptr [ebx]
```