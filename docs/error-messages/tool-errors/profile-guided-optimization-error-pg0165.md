---
title: 按配置文件优化错误 PG0165
description: 介绍读取按配置优化（PGO）数据的 PG0165 错误。
ms.date: 10/30/2019
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: c5e5c5d37f8c70a6c2a3d9f7a43c13bb46d0e25a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626806"
---
# <a name="profile-guided-optimization-error-pg0165"></a>按配置文件优化错误 PG0165

读取按配置优化的数据时出错。 此错误可能以多种形式出现：

> 读取 "*filename .pgd*"：不支持 "pgd 版本（版本不匹配）"。

PGD 文件特定于特定的编译器工具集。 如果你使用的编译器不同于用于创建*文件名 .pgd*的编译器，则会生成此错误。 此错误表示此编译器工具集不能使用*文件名 .pgd*中的数据来优化当前程序。 若要解决此问题，请使用当前编译器工具集重新生成*文件名*.pgd。

> 正在读取 "*filename .pgd*"： "pgd 文件是只读的"。

如果文件系统上的 PGD 文件标记为只读，则会显示此错误。 若要解决此问题，请将文件属性更改为读写。
