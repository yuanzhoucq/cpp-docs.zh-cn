---
title: 错误 C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 3f4d152163d3b21ddf99644c34e63f35ca15e6e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230007"
---
# <a name="fatal-error-c1126"></a>错误 C1126

identifier： 自动分配超过大小

为本地变量的函数 （加上使用的编译器，例如可交换函数的额外 20 字节的空间有限） 分配的空间超过了限制。

若要更正此错误，请使用`malloc`或`new`分配大量的数据。