---
title: 编译器警告（等级 1）C4445
ms.date: 11/04/2016
f1_keywords:
- C4445
helpviewer_keywords:
- C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
ms.openlocfilehash: 6c1b4f4ae4f60d0c4281e0bbcfc9ca2b58d81851
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408103"
---
# <a name="compiler-warning-level-1-c4445"></a>编译器警告（等级 1）C4445

“function”: 在 WinRT 或托管类型中，虚方法不能为私有方法

如果虚函数是私有函数，则它无法由派生类型访问。 若要修复此错误，请将虚拟成员函数的可访问性更改为受保护或公共。