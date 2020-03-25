---
title: 平台默认 cli 命名空间（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: aedb8b7954eaa4bb1cf1060725103cd725c3f180
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181819"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>平台默认 cli 命名空间（C++/CLI 和 C++/CX）

命名空间限定语言元素的名称，使这些名称不与源代码中其他位置的相同名称发生冲突。 例如，名称冲突可能会阻止编译器识别[上下文相关关键字](context-sensitive-keywords-cpp-component-extensions.md)。 命名空间由编译器使用但不保留在已编译的程序集中。

## <a name="all-runtimes"></a>所有运行时

当你创建项目时，Visual Studio 为项目提供默认命名空间。 可以手动重命名此命名空间，但在 C++/CX 中，.winmd 文件名必须与根命名空间的名称匹配。

## <a name="windows-runtime"></a>Windows 运行时

有关详细信息，请参阅[命名空间和类型可见性 (C++/CX)](../cppcx/namespaces-and-type-visibility-c-cx.md)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="syntax"></a>语法

```cpp
using namespace cli;
```

### <a name="remarks"></a>备注

C++/CLI 支持 cli 命名空间。 使用 `/clr` 进行编译时，“语法”部分中的 using 语句是隐式的。

cli 命名空间包含以下语言功能：

- [数组](arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)

- [safe_cast](safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的代码示例展示了可以将 cli 命名空间中的符号用作代码中的用户定义符号。  不过，一旦这样做，必须显式或隐式限定对同名 cli 语言元素的引用。

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
