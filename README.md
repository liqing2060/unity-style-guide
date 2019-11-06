# Unity工程规范

本文改编自[Unity工程规范](https://github.com/luochuanyuewu/unity-style-guide)，介绍了Unity的工程使用规范，适用于程序、策划、美术等所有Unity开发人员。

<a name="toc"></a>
## 目录

> 1. [资源命名约定](#anc)
> 1. [目录结构](#structure)

<a name="anc"></a>
<a name="1"></a>
## 1. 资源命名约定

应该严格遵守该约定，以便于资源的使用和维护。

<a name="base-asset-name"></a>
<a name="1.1"></a>
### 1.1 基本命名规则

基本格式：`Prefix_BaseAssetName_Variant_Suffix`，即 `前缀_基本资源名_拓展名_后缀`，详解：

前缀`Prefix` 和 后缀`Suffix` 由资源类型确定，具体请参照[资源类型表](#asset-name-modifiers)。

基本资源名`BaseAssetName` 表明了资源在逻辑关系上属于谁，命名上应简短、便于记忆。  
例如，有个角色叫Bob，那么所有和Bob相关的资源的`BaseAssetName`都应该叫做`Bob`。

扩展名`Varient`用来保证资源的唯一性。  
例如，Bob有多套皮肤，则相关资源的名字可以是`Bob_Evil`、`Bob_Retro`。  
若仅是为了保证资源的唯一性，`Varient`可以使用从`01`开始的两位数字来表示，例如，`Rock_01`、`Rock_02`等。  
基于你所制作的资源扩展属性，你可以把多个扩展名串联起来，例如，`Bob_Evil_01`、`Bob_Evil_02`。

<a name="1.1-examples"></a>
#### 1.1 范例

##### 1.1e1 Bob

| 资源类型                | 资源名                                                     |
| ----------------------- | ---------------------------------------------------------- |
| Skinned Mesh           | SK_Bob                                                     |
| Material                | M_Bob                                                      |
| Texture (Diffuse/Albedo)| T_Bob_D                                                    |
| Texture (Normal)        | T_Bob_N                                                    |
| Texture (Evil Diffuse)  | T_Bob_Evil_D                                               |

##### 1.1e2 Rocks

| 资源类型                | 资源名                                                     |
| ----------------------- | ---------------------------------------------------------- |
| Static Mesh (01)        | S_Rock_01                                                  |
| Static Mesh (02)        | S_Rock_02                                                  |
| Static Mesh (03)        | S_Rock_03                                                  |

<a name="asset-name-modifiers"></a>
<a name="1.2"></a>
### 1.2 资源类型表

资源命的前缀和后缀请参照以下表格。

#### 目录

> 1.2.1 通用 [Common](#anc-common)  
> 1.2.2 动作 [Animations](#anc-animations)  
> 1.2.5 材质 [Materials](#anc-materials)  
> 1.2.6 纹理 [Textures](#anc-textures)  
> 1.2.7 杂项 [Miscellaneous](#anc-misc)  
> 1.2.8 精灵 [Sprites](#anc-paper2d)  
> 1.2.9 物理 [Physics](#anc-physics)  
> 1.2.10 声音 [Sound](#anc-sound)  
> 1.2.11 界面 [UI](#anc-ui)  
> 1.2.12 特效 [Effects](#anc-effects)  

<a name="anc-common"></a>
<a name="1.2.1"></a>
#### 1.2.1 通用
| 资源类型                | 前缀       | 后缀       | 备注                             |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Scene                   |            |            | [所有场景应该放在Scenes目录下](#2.4) |
| Material                | M_         |            |                                  |
| Static Mesh             | S_         |            |                                  |
| Skinned Mesh            | SK_        |            |                                  |
| Texture                 | T_         | _?         | 后缀参照[纹理](#anc-textures)     |
| Particle System         | PS_        |            |                                  |
| Canvas                  | UI_        |            |                                  |

<a name="anc-animations"></a>
<a name="1.2.2"></a>
#### 1.2.2 动作

| 资源类型                | 前缀       | 后缀       | 备注                             |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Animator Controller   | AC_       |               |   
| Animator Override Controller      | AOC_          |            |            
| Animation             | AM_  |                    | 
| Skinned Mesh           | SK_        |            |                                  |


<a name="anc-materials"></a>
<a name="1.2.5"></a>
### 1.2.5 材质

| 资源类型                | 前缀       | 后缀       | 备注                             |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Material                | M_         |            |                                  |
| Shader |     SD_        |            |            |                                  |
| Physical Materials      | PM_        |            |                                  |

<a name="anc-textures"></a>
<a name="1.2.6"></a>
### 1.2.6 纹理

| 资源类型                | 前缀       | 后缀       | 备注                             |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Texture                 | T_         |            |                                  |
| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Texture (Normal)        | T_         | _N         |                                  |
| Texture (Roughness)     | T_         | _R         |                                  |
| Texture (Alpha/Opacity) | T_         | _A         |                                  |
| Texture (Ambient Occlusion) | T_     | _O         |                                  |
| Texture (Bump)          | T_         | _B         |                                  |
| Texture (Emissive)      | T_         | _E         |                                  |
| Texture (Mask)          | T_         | _M         |                                  |
| Texture (Specular)      | T_         | _S         |                                  |
| Texture (Packed)        | T_         | _*         |                                   |
| Texture Cube            | TC_        |            |                                  |
| Media Texture           | MT_        |            |                                  |
| Render Texture           | RT_        |            |                                  |
| Cube Render Texture      | RTC_       |            |                                  |

<a name="1.2.6.1"></a>
#### 1.2.6.1 纹理合并
纹理合并是很常见的方法，比如通常可以把自发光(Emissive)、粗糙度(Roughness)、环境光(Ambient Occlusion)以RGB通道的形式保存在纹理中，然后在文件的后缀中，注明这些信息，例如`_EGO`。

<a name="anc-misc"></a>
<a name="1.2.7"></a>
### 1.2.7 杂项

| 资源类型                | 前缀       | 后缀       | 备注                             |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Playables Behavior  | PB_       |            |                                  |
| Playables Assets  | PA_       |            |                                  |

<a name="anc-paper2d"></a>
<a name="1.2.8"></a>
### 1.2.8 2D

| 资源类型                | 前缀       | 后缀       | 备注                             |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Sprite                  | SP_        |            |                                  |
| Sprite Atlas Group      | SPG_       |            |                                  |
| Tile Map                | TM_        |            |                                  |

<a name="anc-physics"></a>
<a name="1.2.9"></a>
### 1.2.9 物理

| 资源类型                | 前缀       | 后缀       | 备注                             |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Physical Material       | PM_        |            |                                  |
| Destructible Mesh       | DM_        |            |                                  |

<a name="anc-sounds"></a>
<a name="1.2.10"></a>
### 1.2.10 声音

| 资源类型                | 前缀       | 后缀       | 备注                             |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Audio Mixer             | Mix_       |            |                                  |
| Sound Wave              | A_         |            |                                  |

<a name="anc-ui"></a>
<a name="1.2.11"></a>
### 1.2.11 界面

| 资源类型                | 前缀       | 后缀       | 备注                             |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Font                    | Font_      |            |                                  |

<a name="anc-effects"></a>
<a name="1.2.12"></a>
### 1.2.12 Effects

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Particle System         | PS_        |            |                                  |
| Material (Post Process) | PP_        |            |                                  |

<a name="2"></a>
<a name="structure"></a>
## 2. 目录结构

在本套规范中，我们尽量利用了Unity的Project视图的**过滤**和**搜索**功能来查找资源，而不是按照资源类型来划分目录结构。

> 如果你正确遵守了前面使用前缀的资源[命名规范](#1.2)，那么就没有必要按照资源类型创建`Meshes`、`Textures`和 `Materials`这样的目录结构，因为你可以在过滤器中通过前缀来找到特定类型的资源。

<a name="2e1"><a>
### 2e1 目录结构示例
<pre>
|-- Assets
    |-- <a href="#2.2">Fairytale</a>
        |-- Art
        |   |-- Industrial
        |   |   |-- Ambient
        |   |   |-- Machinery
        |   |   |-- Pipes
        |   |-- Nature
        |   |   |-- Ambient
        |   |   |-- Foliage
        |   |   |-- Rocks
        |   |   |-- Trees
        |   |-- Office
        |-- Characters
        |   |-- Bob
        |   |-- Common
        |   |   |-- <a href="#2.7">Animations</a>
        |   |   |-- Audio
        |   |-- Jack
        |   |-- Steve
        |   |-- <a href="#2.1.3">Zoe</a>
        |-- <a href="#2.5">Core</a>
        |   |-- Characters
        |   |-- Engine
        |   |-- <a href="#2.1.2">GameModes</a>
        |   |-- Interactables
        |   |-- Pickups
        |   |-- Weapons
        |-- Effects
        |   |-- Electrical
        |   |-- Fire
        |   |-- Weather
        |-- <a href="#2.4">Scenes</a>
        |   |-- Level1
        |   |-- Level2
        |-- <a href="#2.8">MaterialLibrary</a>
        |   |-- Debug
        |   |-- Metal
        |   |-- Paint
        |   |-- Utility
        |   |-- Weathering
        |-- Placeables
        |   |-- Pickups
        |-- Weapons
            |-- Common
            |-- Pistols
            |   |-- DesertEagle
            |   |-- RocketPistol
            |-- Rifles
</pre>

使用这种目录结构的原因如下：

### 目录

> 2.1 文件夹命名 [Folder Names](#structure-folder-names)  
> 2.2 顶层目录 [Top-Level Folders](#structure-top-level)  
> 2.3 开发者目录 [Developer Folders](#structure-developers)  
> 2.4 场景目录 [Scenes](#structure-Scenes)  
> 2.5 核心资源 [Core](#structure-core)  
> 2.6  [避免以`Assets` 或 `AssetTypes`命名](#structure-assettypes)  
> 2.7 超大资源 [Large Sets](#structure-large-sets)  
> 2.8 材质库 [Material Library](#structure-material-library)  

<a name="2.1"></a>
<a name="structure-folder-names"></a>
### 2.1 文件夹命名

关于文件夹的命名，有一些通用的规范。

<a name="2.1.1"></a>
#### 2.1.1 使用PascalCase大小写规范[<sup>*</sup>](#terms-cases)

所有单词的首字母大写，中间没有任何连接符，例如：`DesertEagle`、`RocketPistol`、 `ASeriesOfWords`。

参照[大小写规范](#terms-cases).

<a name="2.1.2"></a>
#### 2.1.2 不要使用空格

**绝对不要**在目录名中使用空格，空格会导致引擎或工具出现错误。

<a name="2.1.3"></a>
#### 2.1.3 不要使用其他Unicode语言字符或奇怪的符号

在目录名中只使用`a-z`、`A-Z`、`0-9`这些安全的字符，`@`、`-`、`_`、`,`、`*`、`#`等字符会引发异常。

<a name="2.2"></a>
<a name="structure-top-level"></a>
### 2.2 使用一个顶级目录来保存所有工程资源

所有工程资源都应该保存在一个以工程名命名的目录中。例如工程叫'Fairytale'，那么工程资源应该保存在`Assets/Fairytale`中。

使用顶级目录的原因：

<a name="2.2.1"></a>
#### 2.2.1 避免全局资源

每个资源都应该有它存在的目的。如果仅仅是为了测试的资源，那么这些资源应该放在[`开发者`](#2.3)目录中。

<a name="2.2.2"></a>
#### 2.2.2 方便资源复用

不同项目共享资源时是通过Unity导出导入package实现的，如此可以避免导入时相同路径的资源被意外覆盖的情况。

<a name="2.2.3"></a>
#### 2.2.3 Unity商店中的资源都是安全的

Unity商店中的资源基本都遵循这个规范，所以可以安全的导入到项目中。例如，NGUI的所有资源都在`Assets/NGUI`目录中，导入和移除都方便安全。

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 开发者目录

用于实验、测试的资源应保存与开发者目录，例如`Assets/Develop/Dee`。开发目录中的资源不得被工程目录使用，如需使用则必须移到工程目录中。

<a name="2.4"></a>
<a name="structure-Scenes"></a>
### 2.4 所有的地图文件应该保存在一个名为'Scenes'的目录中

地图文件非常特殊，几乎所有工程都有自己的一套关于地图的命名规则，尤其是使用了sub-levels或者streaming levels技术时。但不管你如何组织自己的命名规则，都应该把所有地图保存在`/Assets/ProjectName/Scenes`

记住，尽量使用不浪费大家的时间的方法去解释你的地图如何打开。比如通过子目录的方法去组织地图资源，例如建立 `Scenes/Campaign1/` 或 `Scenes/Arenas`，但最重要的是一定要都放在`/Assets/Project/Scenes`

这也有助于产品的打版本工作，如果工程里的地图保存的到处都是，版本工程师还要到处去找，就让人很恼火了，而把地图放在一个地方，做版本时就很难漏掉某个地图，对于烘培光照贴图或者质量检查都有利。

<a name="2.5"></a>
<a name="structure-core"></a>
### 2.5 使用`Core`目录存储核心代码资源以及其他文件资源

使用`/Assets/Project/Core`这个目录用来保存一个工程中最为核心的资源。例如，非常基础的`Manager`, `Character`, `PlayerController`, `Sington`, `PlayerState`，以及如此相关的一些资源也应该放在这里。

这个目录非常明显的告诉其他团队成员:"不要碰我！"。非引擎程序员很少有理由去碰这个目录，如果工程目录结构合理，那么游戏设计师只需要使用子类提供的功能就可以工作，负责场景编辑的员工只需要使用专用的Prefab就可以，而不用碰到这些基础类。

例如，如果项目需要设计一种可以放置在场景中并且可以被捡起的物体，那么应该首先设计一个具有被捡起功能的基类放在`Core/Pickups`目录中，而各种具体的可以被捡起的物体诸如药瓶、子弹这样的物体，应该放在`/Assets/Project/Placeables/Pickups/`这样的目录中。游戏设计师可以在这些目录中定义和设计这些物体，所以他们不应该去碰`Core/Pickups`目录下的代码，要不然可能无意中破坏工程中的其他功能

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 不要创建名为`Assets` 或者 `AssetTypes`的目录

<a name="2.6.1"></a>
#### 2.6.1 创建一个名为`Assets`的目录是多余的。

因为本来所有目录就是用来保存资源的

<a name="2.6.2"></a>
#### 2.6.2 创建名为`Meshes`、 `Textures`或者`Materials`的目录是多余的。

资源的文件名本身已经提供了资源类型信息，所以在目录名中再提供资源类型信息就是多余了，而且使用资源浏览器的过滤功能，可以非常便利的提供相同的功能。

比如想查看`Environment/Rocks/`目录下所有的静态Mesh资源？只要打开静态Mesh过滤器就可以了，如果所有资源的文件名已经正确命名，这些文件还会按照文件名和前缀正确排序，如果想查看所有静态Mesh和带有骨骼的Mesh资源，只要打开这两个过滤器就可以了，这种方法要比通过打开关闭文件夹省事多了。

> 这种方法也能够节省路径长度，因为用前缀`S_`只有两个字符，要比使用`Meshes/`七个字符短多了。

这么做其实也能防止有人把Mesh或者纹理放在`Materials`目录这种愚蠢行为。

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 超大资源要有自己的目录结构

这节可以视为针对[2.6](#2.6)的补充

有一些资源类型通常文件数量巨大，而且每个作用都不同。典型的例子是动画资源和声音资源。如果你发现有15个以上的资源属于同一个逻辑类型，那么它们应该被放在一起。

举例来说，角色共用的动画资源应该放在`Characters/Common/Animations`目录中，并且其中应该还有诸如`Locomotion` 或者`Cinematic`的子目录

> 这并不适用与纹理和材质。比如`Rocks`目录通常会包含数量非常多的纹理，但每个纹理都都是属于特定的石头的，它们应该被正确命名就足够了。即使这些纹理属于[材质库](#2.8)

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 材质库`MaterialLibrary`

如果你的工程中使用了任何基础材质、分层材质，或者任何被重复使用而不属于特定模型的材质和纹理，这些资源应该放在材质库目录`Assets/Project/MaterialLibrary`。

这样可以很容易管理这些'全局'材质

> 这也使得'只是用材质实例'这个原则得以执行的比较容易。如果所有的美术人员都只是用材质实例，那么所有的原始材质都应该保存在这个目录中。你可以通过搜索所有不在`MaterialLibrary`中的基础材质来验证这一点。

`MaterialLibrary`这个目录并不是仅能保存材质资源，一些共用的工具纹理、材质函数以及其他具有类似属性的资源都应该放在这个目录或子目录中。例如，噪声纹理应该保存在`MaterialLibrary/Utility`目录中。

任何用来测试或调试的材质应该保存在`MaterialLibrary/Debug`中，这样当工程正式发布时，可以很容易把这些材质从删除，因为这些材质如果不删除，可能在最终产品中非常扎眼。


## 专业术语

<a name="terms-cases"></a>
##### Cases(大小写）

对于字母大小写的规范有数种，以下是几种常见的几种

> ###### PascalCase
>
> 每个单词的首字母都是大写，单词之间没有其他字符，例如 ：`DesertEagle`, `StyleGuide`, `ASeriesOfWords`。
> 
> ###### camelCase
>
> 第一个单词的首字母小写，后面的单词的首字母大写，例如：`desertEagle`, `styleGuide`, `aSeriesOfWords`。
>
> ###### Snake_case
>
> 单词之间用下划线链接，单词的首字母可以大写也可以小写，例如：`desert_Eagle`, `Style_Guide`, `a_Series_of_Words`