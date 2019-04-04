---
title: 图形 (C++ AMP)
ms.date: 11/04/2016
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
ms.openlocfilehash: 4a40575d84c9a0efedcb3c7c9717fc310870b530
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260876"
---
# <a name="graphics-c-amp"></a>图形 (C++ AMP)

C + + AMP 中包含一些 Api [concurrency:: graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md)可用于访问在 Gpu 的纹理支持的命名空间。 一些常见的情况有：

- 可以使用[纹理](../../parallel/amp/reference/texture-class.md)类作为计算和利用漏洞攻击的数据容器*空间局部性*的纹理缓存和 GPU 硬件的布局。 空间局部性是相距较近的数据元素的属性。

- 运行时可以实现与非计算着色器的高效互操作。 像素、顶点、分割和外壳着色器经常使用或生成一些可在你的 C++ AMP 计算中使用的纹理。

- C++ AMP 中的图形 API 提供访问子字已打包缓冲区的替代方法。 纹理格式代表*纹素*（纹理元素） 的组成的 8 位或 16 位标量允许访问此类已打包的数据存储。

## <a name="the-norm-and-unorm-types"></a>norm 和 unorm 类型

`norm`并`unorm`类型是标量类型的限制的范围**float**值; 这称为*夹紧*。 这些类型可从其他标量类型显式构造。 在强制转换时，值首先转换为**float** ，然后限制到 norm [-1.0，1.0] 或 unorm [0.0，1.0] 允许的各自区域。 从 +/- 无穷强制转换时将返回 +/-1。 未定义从 NaN 的强制转换。 可以从 unorm 隐式构造 norm，而且不会丢失数据。 这些类型已定义到浮点类型的隐式转换运算符。 这些类型和其他内置标量类型之间等定义二元运算符**float**并**int**: +、-， \*，/、 = =、 ！ =，>， \<，> =、 < =。 此外支持复合赋值运算符: + =、-=、 \*=、 / =。 Norm 类型已定义一元求反运算符 (-)。

## <a name="short-vector-library"></a>短矢量库

短矢量库提供的功能的某些[矢量类型](http://go.microsoft.com/fwlink/p/?linkid=248500)的 HLSL 中定义，通常用于定义纹素。 短矢量是一种可保留 1-4 个相同类型值的数据结构。 支持的类型为**双**， **float**， **int**， `norm`， `uint`，和`unorm`。 下表中显示了这些类型名称。 对于每种类型，没有也相应**typedef** ，没有下划线在名称中。 具有下划线的类型[concurrency:: graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md)。 没有下划线的类型[Concurrency::graphics::direct3d Namespace](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md) ，以便它们明确区分的命名方式类似的基础类型如 **__int8**并 **__int16**。

||长度 2|长度为 3|长度为 4|
|-|--------------|--------------|--------------|
|double|double_2<br /><br /> double2|double_3<br /><br /> double3|double_4<br /><br /> double4|
|float|float_2<br /><br /> float2|float_3<br /><br /> float3|float_4<br /><br /> float4|
|int|int_2<br /><br /> int2|int_3<br /><br /> int3|int_4<br /><br /> int4|
|norm|norm_2<br /><br /> norm2|norm_3<br /><br /> norm3|norm_4<br /><br /> norm4|
|uint|uint_2<br /><br /> uint2|uint_3<br /><br /> uint3|uint_4<br /><br /> uint4|
|unorm|unorm_2<br /><br /> unorm2|unorm_3<br /><br /> unorm3|unorm_4<br /><br /> unorm4|

### <a name="operators"></a>运算符

如果在两个短矢量之间定义一个运算符，则也会在短矢量和标量之间定义此运算符。 此外，必须符合以下条件之一：

- 标量的类型必须与短矢量的元素类型相同。

- 通过使用用户定义的转换，可将标量的类型隐式转换为矢量的元素类型。

运算是在短矢量和标量的每个组件之间进行的组件级运算。 以下一些有效的运算符：

|运算符类型|有效类型|
|-------------------|-----------------|
|二元运算符|对所有类型有效: +、-， \*，/，<br /><br /> 对整数类型有效: %、 ^、 &#124;，&，<\<，>><br /><br /> 两个矢量必须具有相同的大小，而结果将是相同大小的矢量。|
|关系运算符|对所有类型有效：== 和 !=|
|复合赋值运算符|对所有类型有效: + =、-=、 \*=、 / =<br /><br /> 对整数类型有效: %=、 ^ =、 &#124;=、 & =、 <\<=、 >> =|
|递增和递减运算符|对所有类型有效：++、--<br /><br /> 前缀和后缀均有效。|
|位非运算符 (~)|对整数类型有效。|
|一元 - 运算符|对除 `unorm` 和 `uint` 外的所有类型有效。|

### <a name="swizzling-expressions"></a>Swizzling 表达式

短矢量库支持 `vector_type.identifier` 访问器构造来访问短矢量的组件。 `identifier`，这被称为*swizzling 表达式*，指定矢量的组件。 此表达式可以是左值或右值。 在标识符中的各个字符可能是： x、 y、 z 和 w;或 r、 g、 b、 和。 "x"和"r"表示第零个组件、"y"和"g"表示第一个组件等。 （请注意，“x”和“r”不能在同一标识符中使用。）因此，“rgba”和“xyzw”将返回相同的结果。 诸如“x”和“y”等单组件访问器属于标量值类型。 多组件访问器属于短矢量类型。 例如，如果构造一个名为 `int_4` 且值为 2、4、6、8 的 `fourInts` 矢量，则 `fourInts.y` 将返回整数 4，而 `fourInts.rg` 将返回一个值为 2、4 的 `int_2` 对象。

## <a name="texture-classes"></a>纹理类

许多 GPU 具有已进行优化的硬件和缓存，适用于获取像素和纹素以及呈现图像和纹理。 [纹理\<T，N >](../../parallel/amp/reference/texture-class.md)类，该类是纹素对象的容器类，公开这些 Gpu 的纹理功能。 纹素可以是：

- **Int**， `uint`， **float**， **double**， `norm`，或`unorm`标量。

- 具有两个或四个组件的短矢量。 唯一的例外是 `double_4`，不允许使用此短矢量。

`texture` 对象的秩可以是 1、2 或 3。 在 `texture` 调用的 lambda 中，`parallel_for_each` 对象只能通过引用来捕获。 纹理存储作为 Direct3D 纹理对象存储在 GPU 中。 有关纹理和纹素在 Direct3D 中的详细信息，请参阅[Direct3D 11 中的纹理简介](http://go.microsoft.com/fwlink/p/?linkid=248502)。

你所使用的纹素类型可以是图形编程中使用的众多纹理格式中的一种。 例如，RGBA 格式可以使用 32 位，其中，R、G、B 和 A 标量元素各 8 位。 图形卡的纹理硬件可以访问基于格式的各个元素。 例如，如果你使用的是 RGBA 格式，则纹理硬件可以提取每个 8 位组件形成 32 位窗体。 在 C++ AMP 中，你可以设置每个纹理标量元素的位数，以便自动访问代码中的各个标量元素，而不必进行移位。

### <a name="instantiating-texture-objects"></a>实例化纹理对象

你可以声明纹理对象而不初始化。 下面的代码示例声明了多个纹理对象。

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextures() {
    // Create a 16-texel texture of int.
    texture<int, 1> intTexture1(16);
    texture<int, 1> intTexture2(extent<1>(16));

    // Create a 16 x 32 texture of float_2.
    texture<float_2, 2> floatTexture1(16, 32);
    texture<float_2, 2> floatTexture2(extent<2>(16, 32));

    // Create a 2 x 4 x 8 texture of uint_4.
    texture<uint_4, 3> uintTexture1(2, 4, 8);
    texture<uint_4, 3> uintTexture2(extent<3>(2, 4, 8));
}
```

你还可以使用构造函数来声明和初始化 `texture` 对象。 下面的代码示例从 `texture` 对象的一个矢量实例化了一个 `float_4` 对象。 每个标量元素的位数设置为默认值。 你不能将此构造函数用于 `norm`、`unorm` 或 `norm` 及 `unorm` 的短矢量，因为它们的每标量元素位数不是默认值。

```cpp
#include <amp.h>
#include <amp_graphics.h>
#include <vector>
using namespace concurrency;
using namespace concurrency::graphics;

void initializeTexture() {
    std::vector<int_4> texels;
    for (int i = 0; i < 768 * 1024; i++) {
        int_4 i4(i, i, i, i);
        texels.push_back(i4);
    }

    texture<int_4, 2> aTexture(768, 1024, texels.begin(), texels.end());
}
```

通过使用指针指向源数据、源数据的字节大小和每标量元素位数的构造函数重载，你可以声明和初始化 `texture` 对象。

```cpp
void createTextureWithBPC() { // Create the source data.
    float source[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        source[i] = (float)i;
    }
    // Initialize the texture by using the size of source in bytes // and bits per scalar element.
    texture<float_2, 1> floatTexture(1024, source, (unsigned int)sizeof(source), 32U);
}
```

这些示例中的纹理是在默认快捷键的默认视图中创建的。 如果要指定 `accelerator_view` 对象，则可以使用构造函数的其他重载。 你不能在 CPU 快捷键上创建纹理对象。

如下表所示，`texture` 对象的每个维度具有大小限制。 如果超出限制，就会产生运行时错误。

|纹理|每个维度的大小限制|
|-------------|---------------------|
|纹理\<T 1 >|16384|
|纹理\<T，2 >|16384|
|纹理\<T，3 >|2048|

### <a name="reading-from-texture-objects"></a>读取纹理对象

你可以从读取`texture`通过使用对象[texture:: operator\[\]](reference/texture-class.md#operator_at)，[纹理:: operator （) 运算符](reference/texture-class.md#operator_call)，或[texture:: get 方法](reference/texture-class.md#get). 两个运算符将返回一个值，而不是引用。 因此，你不能使用 `texture` 写入 `texture::operator\[\]` 对象。

```cpp
void readTexture() {
    std::vector<int_2> src;
    for (int i = 0; i <16 *32; i++) {
        int_2 i2(i, i);

        src.push_back(i2);
    }

    std::vector<int_2> dst(16* 32);

    array_view<int_2, 2> arr(16, 32, dst);

    arr.discard_data();

    const texture<int_2, 2> tex9(16, 32, src.begin(), src.end());

    parallel_for_each(tex9.extent, [=, &tex9] (index<2> idx) restrict(amp) { // Use the subscript operator.
        arr[idx].x += tex9[idx].x; // Use the function () operator.
        arr[idx].x += tex9(idx).x; // Use the get method.
        arr[idx].y += tex9.get(idx).y; // Use the function () operator.
        arr[idx].y += tex9(idx[0], idx[1]).y;
    });

    arr.synchronize();
}
```

下面的代码示例演示如何在短矢量中存储纹理通道，然后访问作为短矢量属性的各个标量元素。

```cpp
void UseBitsPerScalarElement() { // Create the image data. // Each unsigned int (32-bit) represents four 8-bit scalar elements(r,g,b,a values).
    const int image_height = 16;
    const int image_width = 16;
    std::vector<unsigned int> image(image_height* image_width);

    extent<2> image_extent(image_height, image_width);

    // By using uint_4 and 8 bits per channel, each 8-bit channel in the data source is // stored in one 32-bit component of a uint_4.
    texture<uint_4, 2> image_texture(image_extent, image.data(), image_extent.size()* 4U,  8U);

    // Use can access the RGBA values of the source data by using swizzling expressions of the uint_4.
    parallel_for_each(image_extent,
        [&image_texture](index<2> idx) restrict(amp)
        { // 4 bytes are automatically extracted when reading.
            uint_4 color = image_texture[idx];
            unsigned int r = color.r;
            unsigned int g = color.g;
            unsigned int b = color.b;
            unsigned int a = color.a;
        });
}
```

下表列出了每种短矢量类型的每通道有效位数。

|纹理数据类型|每标量元素的有效位数|
|-----------------------|-----------------------------------|
|int、int_2、int_4<br /><br /> uint、uint_2、uint_4|8, 16, 32|
|int_3、uint_3|32|
|float、float_2、float_4|16, 32|
|float_3|32|
|double、double_2|64|
|norm、norm_2、norm_4<br /><br /> unorm、unorm_2、unorm_4|8, 16|

### <a name="writing-to-texture-objects"></a>写入纹理对象

使用[texture:: set](reference/texture-class.md#set)方法将写入`texture`对象。 纹理对象可以是只读或读/写属性。 纹理对象若要可读写，必须满足以下条件：

- T 只有一个标量组件。 （不允许使用短矢量。）

- T 不是**双**， `norm`，或`unorm`。

- `texture::bits_per_scalar_element` 属性为 32。

如果不符合这三个条件，则 `texture` 对象为只读对象。 编译期间将检查前两个条件。 如果有代码尝试写入 `readonly` 纹理对象，将产生编译错误。 为条件`texture::bits_per_scalar_element`在运行时，检测，并在运行时生成[unsupported_feature](../../parallel/amp/reference/unsupported-feature-class.md)异常，如果尝试写入只读`texture`对象。

下面的代码示例向一个纹理对象写入了多个值。

```cpp
void writeTexture() {
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {
        tex1.set(idx, 0);
    });
}
```

### <a name="copying-texture-objects"></a>复制纹理对象

可通过使用纹理对象之间复制[副本](reference/concurrency-namespace-functions-amp.md#copy)函数或[copy_async](reference/concurrency-namespace-functions-amp.md#copy_async)函数，如下面的代码示例中所示。

```cpp
void copyHostArrayToTexture() { // Copy from source array to texture object by using the copy function.
    float floatSource[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        floatSource[i] = (float)i;
    }
    texture<float_2, 1> floatTexture(1024);

    copy(floatSource, (unsigned int)sizeof(floatSource), floatTexture);

    // Copy from source array to texture object by using the copy function.
    char charSource[16* 16];
    for (int i = 0; i <16* 16; i++) {
        charSource[i] = (char)i;
    }
    texture<int, 2> charTexture(16, 16, 8U);

    copy(charSource, (unsigned int)sizeof(charSource), charTexture);
    // Copy from texture object to source array by using the copy function.
    copy(charTexture, charSource, (unsigned int)sizeof(charSource));
}
```

也可以复制从一个纹理到另一个使用[texture:: copy_to](reference/texture-class.md#copy_to)方法。 这两个纹理可以位于不同的 accelerator_view 上。 当复制到 `writeonly_texture_view` 对象时，数据将复制到基础 `texture` 对象。 源和目标 `texture` 对象上的每标量元素位数和范围必须相同。 如果不符合这些需求，运行时将引发异常。

## <a name="texture-view-classes"></a>纹理视图类

引入了 c + + AMP [texture_view 类](../../parallel/amp/reference/texture-view-class.md)Visual Studio 2013 中。 纹理视图支持相同的纹素类型和为排名[texture 类](../../parallel/amp/reference/texture-class.md)，但与纹理不同，它们提供对其他硬件功能，如纹理采样和 mipmap 访问。 纹理视图支持对基础纹理数据进行只读、只写和读/写访问。

- 只读访问由 `texture_view<const T, N>` 模板专用化提供，支持具有 1 个、2 个或 4 个组件的元素、纹理采样以及动态访问在实例化视图时确定的一系列 mipmap 级别。

- 写入访问由非专用模板类 `texture_view<T, N>` 提供，支持具有 2 个或 4 个组件的元素，并且可以访问在实例化视图时确定的一个 mipmap 级别。 它不支持采样。

- 读写访问由非专用模板类 `texture_view<T, N>` 提供，与纹理一样，支持仅具有 1 个组件的元素；视图可以访问在实例化视图时确定的一个 mipmap 级别。 它不支持采样。

纹理视图类似于数组视图，但不是提供自动数据管理和移动功能， [array_view 类](../../parallel/amp/reference/array-view-class.md)优于[array 类](../../parallel/amp/reference/array-class.md)。 `texture_view` 只能在基础纹理数据所在的快捷键视图中进行访问。

### <a name="writeonlytextureview-deprecated"></a>弃用 writeonly_texture_view

对于 Visual Studio 2013 中，c + + AMP 引入了更好地支持硬件纹理功能，例如采样和 mipmap，无法支持通过[writeonly_texture_view 类](../../parallel/amp/reference/writeonly-texture-view-class.md)。 新引入的 `texture_view` 类支持 `writeonly_texture_view` 中功能的超集；因此，`writeonly_texture_view` 已被弃用。

我们建议（至少在新代码中）使用 `texture_view` 来访问之前由 `writeonly_texture_view` 提供的功能。 请比较下面两个代码示例，这两个示例均会写入具有 2 个组件的纹理对象 (int_2)。 请注意，在这两种情况下，都必须通过 lambda 表达式中的值来捕获视图 `wo_tv4`。 以下是采用新 `texture_view` 类的示例：

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

以下是已弃用的 `writeonly_texture_view` 类：

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

你可以看到，如果只是写入主 mipmap 级别，则两个代码示例几乎完全相同。 如果已在现有代码中使用 `writeonly_texture_view` 并且不打算改进该代码，则不必进行更改。 但是，如果你考虑改进该代码，则我们建议你重写代码以便使用 `texture_view`，因为它的一些改进支持一些新硬件纹理功能。 有关这些新功能的更多信息，请阅读下文。

有关不推荐使用的详细信息`writeonly_texture_view`，请参阅[c + + AMP 中的纹理视图设计概述](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/25/overview-of-the-texture-view-design-in-c-amp.aspx)本机代码博客中的并行编程。

### <a name="instantiating-texture-view-objects"></a>实例化纹理视图对象

声明`texture_view`类似于声明`array_view`相关联**数组**。 下面的代码示例声明了多个`texture`对象以及与之关联的 `texture_view` 对象。

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextureViews()
{
    // Create a 16-texel texture of int, with associated texture_views.
    texture<int, 1> intTexture(16);
    texture_view<const int, 1> intTextureViewRO(intTexture);  // read-only
    texture_view<int, 1> intTextureViewRW(intTexture);        // read-write

    // Create a 16 x 32 texture of float_2, with associated texture_views.
    texture<float_2, 2> floatTexture(16, 32);
    texture_view<const float_2, 2> floatTextureViewRO(floatTexture);  // read-only
    texture_view<float_2, 2> floatTextureViewRO(floatTexture);        // write-only

    // Create a 2 x 4 x 8 texture of uint_4, with associated texture_views.
    texture<uint_4, 3> uintTexture(2, 4, 8);
    texture_view<const uint_4, 3> uintTextureViewRO(uintTexture);  // read-only
    texture_view<uint_4, 3> uintTextureViewWO(uintTexture);        // write-only
}
```

请注意，为何元素类型为非常量且具有一个组件的纹理视图为读写属性，而元素类型为非常量但具有多个组件的纹理视图却是只写属性。 常量元素类型的纹理视图始终是只读属性，但如果元素类型为非常量，则元素中的组件数量决定了视图为读写（1 个组件）视图还是只写（多个组件）视图。

在决定视图是否支持纹理采样以及 mipmap 级别的访问方式时，`texture_view` 的元素类型（其常量性及其组件数）也会发挥一定的作用：

|类型|组件数|读取|Write|采样|Mipmap 访问|
|----------|----------------|----------|-----------|--------------|-------------------|
|texture_view\<const T，N >|1, 2, 4|是|否 (1)|是|是，可索引。 范围在实例化时确定。|
|Texture_view\<T，N >|1<br /><br /> 2, 4|是<br /><br /> 否 （2)|是<br /><br /> 是|否 (1)<br /><br /> 否 (1)|是，一个级别。 级别在实例化时确定。<br /><br /> 是，一个级别。 级别在实例化时确定。|

通过此表，你可以看到只读纹理视图完全支持新功能，以此换取不能写入视图。 可写纹理视图的限制在于它们只能访问一个 mipmap 级别。 读写纹理视图的专用性甚至高于可写纹理视图，因为它们增加了一项要求，即纹理视图的元素类型应只有一个组件。 请注意，可写纹理视图不支持采样，因为采样是面向读取的操作。

### <a name="reading-from-texture-view-objects"></a>读取纹理视图对象

通过纹理视图读取未采样的纹理数据类似于从纹理本身读取数据，只是纹理是通过引用来捕获，而纹理视图则是通过值来捕获。 下面两个代码示例进行了演示；首先，仅使用 `texture`：

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {
        tex_data.set(idx, int_2(1, 1));
    });
}
```

以下是同一个示例，只是现在使用 `texture_view` 类：

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        tex_view.set(idx, int_2(1, 1));
    });
}
```

元素基于浮点类型（例如，float、float_2 或 float_4）的纹理视图也可以使用纹理采样来读取，以便利用对各种筛选模式和寻址模式的硬件支持。 C++ AMP 支持计算情景下两种最常见的筛选模式，即点筛选（最近邻域）和线性筛选（加权平均），同时支持四种寻址模式，即重叠寻址、镜像寻址、钳位寻址和边框寻址。 有关寻址模式的详细信息，请参阅[address_mode 枚举](reference/concurrency-graphics-namespace-enums.md#address_mode)。

除了 C++ AMP 直接支持的模式外，你还可以访问底层平台的其他筛选模式和寻址模式，方法是使用互操作 API 采用通过平台 API 直接创建的纹理采样器。 例如，Direct3D 支持各向异性筛选等其他筛选模式，并可以对纹理的各个维度应用不同的寻址模式。 通过使用 Direct3D API，你可以创建一个坐标为纵向重叠、横向镜像并进行各向异性筛选采样的纹理采样器，然后通过 `make_sampler` 互操作 API 利用 C++ AMP 代码中的采样器。 有关详细信息请参阅[c + + AMP 中的纹理采样](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/18/texture-sampling-in-c-amp.aspx)本机代码博客中的并行编程。

纹理视图还支持读取 mipmap。 只读纹理视图（具有常量元素类型的视图）可以提供最大的灵活性，原因在于可对实例化时确定的一系列 mip 级别进行动态采样，而且支持具有 1、2 或 4 个组件的元素。 元素仅具有一个组件的读写纹理视图也支持 mipmap，但仅限实例化时确定的一个 mipmap 级别。 有关详细信息，请参阅[具有 Mipmap 的纹理](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/08/22/texture-with-mipmaps.aspx)本机代码博客中的并行编程。

### <a name="writing-to-texture-view-objects"></a>写入纹理视图对象

使用[texture_view:: get 方法](reference/texture-view-class.md#get)要写入到基础`texture`通过`texture_view`对象。 纹理视图可以为只读、读写或只写视图。 纹理视图若要可写，则必须具有非常量元素类型；纹理视图若要可读写，则其元素类型还必须只有一个组件。 否则，纹理视图为只读视图。 通过纹理视图一次只能访问一个纹理 mipmap 级别，此级别将在实例化视图时指定。

此示例演示如何写入纹理（具有 4 个 mipmap 级别）的第二详细 mipmap 级别。 最详细的 mipmap 级别为级别 0。

```cpp
// Create a texture that has 4 mipmap levels : 16x16, 8x8, 4x4, 2x2
texture<int, 2> tex(extent<2>(16, 16), 16U, 4);

// Create a writable texture view to the second mipmap level :4x4
texture_view<int, 2> w_view(tex, 1);

parallel_for_each(w_view.extent, [=](index<2> idx) restrict(amp)
{
    w_view.set(idx, 123);
});
```

## <a name="interoperability"></a>互操作性

C + + AMP 运行时支持之间的互操作性`texture<T,1>`并[ID3D11Texture1D 接口](http://go.microsoft.com/fwlink/p/?linkId=248503)之间`texture<T,2>`并[ID3D11Texture2D 接口](http://go.microsoft.com/fwlink/p/?linkId=255317)，和之间`texture<T,3>`并[ID3D11Texture3D 接口](http://go.microsoft.com/fwlink/p/?linkId=255377)。 [Get_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture)方法采用`texture`对象，并返回`IUnknown`接口。 [Make_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture)方法采用`IUnknown`接口和一个`accelerator_view`对象，并返回`texture`对象。

## <a name="see-also"></a>请参阅

[double_2 类](../../parallel/amp/reference/double-2-class.md)<br/>
[double_3 类](../../parallel/amp/reference/double-3-class.md)<br/>
[double_4 类](../../parallel/amp/reference/double-4-class.md)<br/>
[float_2 类](../../parallel/amp/reference/float-2-class.md)<br/>
[float_3 类](../../parallel/amp/reference/float-3-class.md)<br/>
[float_4 类](../../parallel/amp/reference/float-4-class.md)<br/>
[int_2 类](../../parallel/amp/reference/int-2-class.md)<br/>
[int_3 类](../../parallel/amp/reference/int-3-class.md)<br/>
[int_4 类](../../parallel/amp/reference/int-4-class.md)<br/>
[norm_2 类](../../parallel/amp/reference/norm-2-class.md)<br/>
[norm_3 类](../../parallel/amp/reference/norm-3-class.md)<br/>
[norm_4 类](../../parallel/amp/reference/norm-4-class.md)<br/>
[short_vector 结构](../../parallel/amp/reference/short-vector-structure.md)<br/>
[short_vector_traits 结构](../../parallel/amp/reference/short-vector-traits-structure.md)<br/>
[uint_2 类](../../parallel/amp/reference/uint-2-class.md)<br/>
[uint_3 类](../../parallel/amp/reference/uint-3-class.md)<br/>
[uint_4 类](../../parallel/amp/reference/uint-4-class.md)<br/>
[unorm_2 类](../../parallel/amp/reference/unorm-2-class.md)<br/>
[unorm_3 类](../../parallel/amp/reference/unorm-3-class.md)<br/>
[unorm_4 类](../../parallel/amp/reference/unorm-4-class.md)
