---
title: MMWORD |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7314c6d0861195e312c7f72481d2e195e041965d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679229"
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