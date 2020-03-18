---
title: 向后兼容性
ms.date: 11/04/2016
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: 2c2b4570e5e3131911e7f424280f16e9977f047e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438561"
---
# <a name="backward-compatibility"></a>向后兼容性

对于产品版本间的兼容性，库 OLDNAMES.LIB 将旧名称映射到新名称。 例如，`open` 将映射到 `_open`。 仅在使用以下命令行选项的组合进行编译时必须显式链接 OLDNAMES.LIB：

- `/Zl`（从对象文件中忽略默认库名称）和 `/Ze`（默认值 - 使用 Microsoft 扩展）

- `/link`（链接器控件）、`/NOD`（无默认库搜索）和 `/Ze`

有关编译器命令行选项的详细信息，请参阅[编译器参考](../build/reference/compiler-options.md)。

## <a name="see-also"></a>另请参阅

[兼容性](../c-runtime-library/compatibility.md)
