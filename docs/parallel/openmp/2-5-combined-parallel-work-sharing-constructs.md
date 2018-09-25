---
title: 2.5 组合的并行工作共享构造 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 45936e5a-c62a-4eea-a8f4-232210c9d0c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c456eceb39d969e6841e3d3bf9028fae4bf5000
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404756"
---
# <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 组合的并行工作共享构造

组合的并行工作共享构造是用于指定包含只有一个工作共享构造的并行区域的快捷方式。 这些指令的语义是相同的显式指定**并行**指令后跟 single 的工作共享构造。

以下部分介绍了组合并行工作共享构造：

- **并行的**指令。

- **并行部分**指令。