---
title: 编译器警告 C4962
ms.date: 11/04/2016
f1_keywords:
- C4962
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
ms.openlocfilehash: a600c1875040e1076978bb80c467e6232303cd82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164841"
---
# <a name="compiler-warning-c4962"></a>编译器警告 C4962

“function”：已禁用按配置文件优化，原因在于优化导致了配置数据文件不一致

函数不是使用 /LTCG:PGO 编译的，因为该函数的计数（分析）数据不可靠。 重做分析以重新生成包含该函数不可靠分析数据的 .pgc 文件。

默认情况下，此警告处于关闭状态。 有关详细信息，请参阅 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
