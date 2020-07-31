---
title: 友元程序集 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
ms.openlocfilehash: a42caaf07f6ec0c71f63d6a0df8a79fff6f737e6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221440"
---
# <a name="friend-assemblies-c"></a>友元程序集 (C++)

对于适用的运行时，*友元程序集*语言功能使得在程序集组件中的命名空间范围或全局范围内的类型可由一个或多个客户端程序集或 netmodule 访问。

## <a name="all-runtimes"></a>所有运行时

**注释**

（并不是所有运行时都支持此语言功能。）

## <a name="windows-runtime"></a>Windows 运行时

**注释**

（Windows 运行时不支持此语言功能。）

### <a name="requirements"></a>要求

编译器选项： **/ZW**

## <a name="common-language-runtime"></a>公共语言运行时

**注释**

#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>使位于程序集组件命名空间范围或全局范围的类型可供客户端程序集或 .netmodule 访问

1. 在组件中，指定程序集特性 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>，然后传递将访问位于组件命名空间范围或全局范围的类型的客户端程序集或 .netmodule 的名称。  您可通过指定其他特性来指定多个客户端程序集或 .netmodule。

1. 在客户端程序集或 .netmodule 中，当你通过使用引用组件程序集时， `#using` 将传递 **`as_friend`** 属性。  如果为 **`as_friend`** 未指定的程序集指定属性 `InternalsVisibleToAttribute` ，则当您尝试在组件中访问命名空间范围或全局范围内的类型时，将引发运行时异常。

如果包含该特性的程序集没有 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 强名称，但使用该特性的客户端程序集具有强名称，则会导致生成错误 **`as_friend`** 。

虽然位于命名空间范围和全局范围的类型可为客户端程序集所知，但成员可访问性仍然有效。  例如，您无法访问私有成员。

必须显式授予对程序集中所有类型的访问权限。  例如，如果程序集 C 引用程序集 B，而程序集 B 具有对程序集 A 中所有类型的访问权限，则程序集 C 没有对程序集 A 中所有类型的访问权限。

有关如何对进行签名（即如何向使用 Microsoft c + + 编译器生成的程序集）进行签名的信息，请参阅[强名称程序集（程序集签名）（c + +/cli）](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。

作为对使用友元程序集功能的替代，您可使用 <xref:System.Security.Permissions.StrongNameIdentityPermission> 限制对单独类型的访问。

### <a name="requirements"></a>要求

编译器选项： **/clr**

### <a name="examples"></a>示例

以下代码示例定义了指定对组件中类型具有访问权限的客户端程序集的组件。

```cpp
// friend_assemblies.cpp
// compile by using: /clr /LD
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type
[assembly:InternalsVisibleTo("friend_assemblies_2")];

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

下一代码示例访问组件中的私有类型。

```cpp
// friend_assemblies_2.cpp
// compile by using: /clr
#using "friend_assemblies.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

下一代码示例定义了未指定将对组件中类型具有访问权限的客户端程序集的组件。

请注意，该组件是使用 **/opt： noref**链接的。 这确保私有类型在组件的元数据中发出，`InternalsVisibleTo` 特性存在时不需要元数据。 有关详细信息，请参阅 [/OPT（优化）](../build/reference/opt-optimizations.md)。

```cpp
// friend_assemblies_3.cpp
// compile by using: /clr /LD /link /opt:noref
using namespace System;

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

以下代码示例定义了尝试访问组件（其未为其私有类型提供访问权限）中私有类型的客户端。 由于运行时的行为，如果您需要捕获异常，则必须尝试访问帮助器函数中的私有类型。

```cpp
// friend_assemblies_4.cpp
// compile by using: /clr
#using "friend_assemblies_3.dll" as_friend
using namespace System;

void Test() {
   Class1 ^ a = gcnew Class1;
}

int main() {
   // to catch this kind of exception, use a helper function
   try {
      Test();
   }
   catch(MethodAccessException ^ e) {
      Console::WriteLine("caught an exception");
   }
}
```

```Output
caught an exception
```

下一代码示例演示了如何创建强名称组件，其指定将对组件中类型具有访问权限的客户端程序集。

```cpp
// friend_assemblies_5.cpp
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type

[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];

private ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

请注意，组件必须指定其公钥。 我们建议您在命令提示符处按顺序运行下列命令以创建密钥对并获取公钥：

**sn-d friend_assemblies .snk**

**sn-k friend_assemblies .snk**

**sn-i friend_assemblies .snk friend_assemblies .snk**

**sn-pc friend_assemblies .snk publickey**

**sn -tp key.publickey**

下一代码示例访问强名称组件中的私有类型。

```cpp
// friend_assemblies_6.cpp
// compile by using: /clr /link /keyfile:friend_assemblies.snk
#using "friend_assemblies_5.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

## <a name="see-also"></a>另请参阅

[适用于运行时平台的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)
