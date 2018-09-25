---
title: Windows 平台 (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility [C++], C run-time libraries
- compatibility [C++], C run-time libraries
- MBCS [C++], Win32 platforms
- operating systems [C++]
- Unicode [C++], Win32 platforms
ms.assetid: 0aacaf45-6dc4-4908-bd52-57abac7b39f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29976d0535d29fce926d7a12b920234548c8a98d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017284"
---
# <a name="windows-platforms-crt"></a>Windows 平台 (CRT)

用于 Visual Studio 的 C 运行时库支持当前版本的 Windows 和 Windows Server、Windows 8、Windows Server 2012、Windows 7、Windows Server 2008 和 Windows Vista；并选择性地支持适用于 x86 的 Windows XP Service Pack 3 (SP3)、适用于 x64 的 Windows XP Service Pack 2 (SP2)，以及同时适用于 x86 和 x64 的 Windows Server 2003 Service Pack 2 (SP2)。 所有这些操作系统都支持 Windows 桌面 API (Win32) 并提供 Unicode 支持。 此外，所有 Win32 应用程序都能使用多字节字符集 (MBCS)。

> [!NOTE]
> 在 Visual Studio 2017 中，“使用 C++ 的桌面开发”工作负载的默认安装不包括对 Windows XP 和 Windows Server 2003 开发的支持。 必须安装可选组件**针对 C++ 的 Windows XP 支持**，用于启用 Windows XP 平台工具集。

## <a name="see-also"></a>请参阅

[兼容性](../c-runtime-library/compatibility.md)
