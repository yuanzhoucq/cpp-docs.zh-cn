---
title: 错误 C1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: e57e4e0899a5f9d81e87a203b1b699cef0884f0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203263"
---
# <a name="fatal-error-c1311"></a>错误 C1311

COFF 格式无法以静态方式初始化使用地址的数字字节的 "var"

在编译时，值未知的地址不能静态分配给类型的变量，其类型的存储小于四个字节。

此错误可能在其他有效C++代码上出现。

以下示例显示了可能导致 C1311 的一种情况。

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```
