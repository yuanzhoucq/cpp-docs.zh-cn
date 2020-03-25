---
title: 编译器警告（等级 1）C4445
ms.date: 11/04/2016
f1_keywords:
- C4445
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
ms.openlocfilehash: 2956758a6bdd074d7fc902c6ebac60af19e34b54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186759"
---
# <a name="compiler-warning-level-1-c4445"></a>编译器警告（等级 1）C4445

“function”: 在 WinRT 或托管类型中，虚方法不能为私有方法

如果虚函数是私有函数，则它无法由派生类型访问。 若要修复此错误，请将虚拟成员函数的可访问性更改为受保护或公共。
