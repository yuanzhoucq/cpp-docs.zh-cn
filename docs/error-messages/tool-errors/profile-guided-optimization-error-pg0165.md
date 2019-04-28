---
title: 按配置文件优化错误 PG0165
ms.date: 11/04/2016
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: f39bbe6540ebec10cd25c41ac2fe9f2acfca9b13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359730"
---
# <a name="profile-guided-optimization-error-pg0165"></a>按配置文件优化错误 PG0165

阅读 Filename.pgd:不支持 PGD 版本 （版本不匹配）。

PGD 文件是特定于特定的编译器工具集。 使用与用于不同的编译器时，会生成此错误*文件名*.pgd。 此错误表示，此编译器工具集不能使用中的数据*文件名*.pgd 来优化当前程序。

若要解决此问题，重新生成*文件名*.pgd 通过使用当前的编译器工具集。