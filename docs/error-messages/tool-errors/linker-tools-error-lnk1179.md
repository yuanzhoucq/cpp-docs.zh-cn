---
title: 链接器工具错误 LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: d85693cec11ef53a6bbbb60d8ced716d2a0bb131
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754345"
---
# <a name="linker-tools-error-lnk1179"></a>链接器工具错误 LNK1179

无效或损坏的文件：重复COMDAT"文件名"

对象模块包含两个或多个具有相同名称的 COMDAT。

此错误可能由使用[/H（](../../build/reference/h-restrict-length-of-external-names.md)限制外部名称的长度）和[/Gy](../../build/reference/gy-enable-function-level-linking.md)（在 COMDATs 中）进行打包函数引起。

## <a name="example"></a>示例

在以下代码中，`function1``function2`在前八个字符中相同。 使用 **/Gy**和 **/H8**编译会产生链接错误。

```cpp
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```
