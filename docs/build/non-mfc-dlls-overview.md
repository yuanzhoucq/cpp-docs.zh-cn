---
title: 非 MFC DLL：概述
ms.date: 11/04/2016
helpviewer_keywords:
- non-MFC DLLs [C++]
- DLLs [C++], non-MFC
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
ms.openlocfilehash: 88afb41205e63a837d7bc134133c3c36eccf5dc1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493174"
---
# <a name="non-mfc-dlls-overview"></a>非 MFC DLL：概述

非 MFC DLL 是不在内部使用 MFC 的 DLL, 并且 DLL 中的导出函数可以由 MFC 或非 MFC 可执行文件调用。 函数通常使用标准 C 接口从非 MFC DLL 导出。

有关非 MFC Dll 的详细信息, 请参阅 Windows SDK 中的[动态链接库](/windows/win32/dlls/dynamic-link-libraries)。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [演练：创建和使用动态链接库](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)

- [从 DLL 导出](exporting-from-a-dll.md)

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [静态链接到 MFC 的规则 MFC Dll](regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC Dll](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL：概述](extension-dlls-overview.md)

## <a name="see-also"></a>请参阅

[DLL 的类型](kinds-of-dlls.md)
