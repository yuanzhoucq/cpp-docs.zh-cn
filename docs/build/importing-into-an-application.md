---
title: 导入到应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- importing DLLs [C++], applications
- applications [C++], importing into
ms.assetid: 9d646466-e12e-4710-8ad9-c819c0375fcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e88d34ce685e22e561683cc33db25997650ed7fd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718376"
---
# <a name="importing-into-an-application"></a>导入到应用程序中

您可以将函数导入应用程序使用两种方法：

- 使用关键字 **__declspec （dllimport)** 主应用程序中函数定义中

- 使用模块定义 (.def) 文件以及 **__declspec （dllimport)**

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 __declspec （dllimport） 的应用程序导入](../build/importing-into-an-application-using-declspec-dllimport.md)

- [使用 __declspec （dllimport） 导入函数调用](../build/importing-function-calls-using-declspec-dllimport.md)

- [导入数据使用 __declspec （dllimport）](../build/importing-data-using-declspec-dllimport.md)

- [使用 DEF 文件导入](../build/importing-using-def-files.md)

## <a name="see-also"></a>请参阅

[导入和导出](../build/importing-and-exporting.md)