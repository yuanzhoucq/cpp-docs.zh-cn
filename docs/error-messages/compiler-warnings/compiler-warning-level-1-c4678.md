---
title: 编译器警告（等级 1）C4678
ms.date: 11/04/2016
f1_keywords:
- C4678
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
ms.openlocfilehash: 9e61d919f08bbbf4f3e74da7ba4f2388516d3152
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374516"
---
# <a name="compiler-warning-level-1-c4678"></a>编译器警告（等级 1）C4678

基类“base_type”的可访问性比“derived_type”低

某个公共类型是从私有类型派生的。 如果在引用的程序集中实例化该公共类型，将无法访问私有基类型的成员。

可能出现 c4678 错误才可访问使用已过时的编译器选项 **/clr: oldsyntax**。 使用时，则会出错 **/clr**来获得可访问性的基类，其派生的类。
