---
title: 链接器工具错误 LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: b18a93c7434ee3d66f42829f373bd916a65369bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195170"
---
# <a name="linker-tools-error-lnk1188"></a>链接器工具错误 LNK1188

BADFIXUPSECTION：：修正目标 "symbol" 无效;可能的零长度部分

在 VxD 链接期间，重定位的目标没有部分。 使用 LINK386 （较旧版本）时，可能已使用 OMF 组记录（由 MASM 组指令生成）将零长度部分与另一个非零长度部分组合在一起。 COFF 格式不支持组指令和长度为零的部分。 当 LINK 自动将此类型的 OMF 对象转换为 COFF 时，可能会发生此错误。
