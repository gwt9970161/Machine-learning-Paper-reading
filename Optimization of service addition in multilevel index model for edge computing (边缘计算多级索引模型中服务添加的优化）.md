# Optimization of service addition in multilevel index model for edge computing (边缘计算多级索引模型中服务添加的优化）

## Abstract

随着边缘计算和人工智能 (AI) 技术的发展，见证了边缘设备以前所未有的数量生成数据。边缘智能（EI）导致边缘设备出现在各种应用领域。EI可以为延迟敏感的应用程序提供高效的服务，其中边缘设备部署为边缘节点来承载大部分执行，可以有效地管理服务并提高服务发现效率。多级索引模型是用于索引服务的众所周知的模型，这种模型正在边缘环境中引入和优化，以在管理大量数据的同时有效地发现服务。然而，通过在动态边缘计算环境中及时准确地添加新服务来有效更新多级索引模型仍然是一个挑战。

针对这个问题，本文提出了一种指定的key选择方法，以提高在多级索引模型中添加服务的效率。我们的实验结果表明，在多级索引模型的部分索引和全索引中，我们的方法与原来的键选择方法相比，分别减少了大约 84% 和 76% 的服务添加时间，减少了大约 78% 和 66% ，分别与随机选择方法相比。与现有最先进的密钥选择方法相比，我们提出的方法显着提高了多级索引模型中的服务添加效率，



## 1. Introduction

实时数据流应用数量的空前增长导致服务架构部署的增加。

存储在大型服务仓库中的服务虽然增加了服务可用性的范围，以满足客户的各种需求，但也增加了网络的负担，因为这种服务模型涉及客户端和云服务器之间的数据通信，从而导致问题例如网络瓶颈、额外延迟和带宽不可用等。

边缘计算正在成为解决传统基于云的服务模型延迟问题的潜在解决方案。[4](https://onlinelibrary.wiley.com/doi/full/10.1002/cpe.6626?saml_referrer=#cpe6626-bib-0004)与将所有数据上传到云服务器相比，边缘计算可以在网络边缘承载相当大比例的流程执行。[5](https://onlinelibrary.wiley.com/doi/full/10.1002/cpe.6626?saml_referrer=#cpe6626-bib-0005)这样的策略可以显着降低网络带宽压力以及数据中心的功耗。

边缘计算吸引了数据密集型和延迟敏感的应用程序，并利用边缘设备从传感器节点收集数据并在可能的情况下在边缘网络中处理收集到的数据的能力。

我们在本文中提出的工作扩展了边缘环境中的多级索引模型，该模型可以有效地管理大数据，并提出了一种指定的键选择方法，其动机是缩小服务检索过程的搜索空间并减少时间开销，而无需影响服务检索过程的稳定性。所提出的密钥选择方法的特点是适应边缘环境中常见的服务动态变化。

主要贡献:

1. 已经提出了一种优化的多级索引模型，用于在动态边缘计算环境中有效地管理和发现服务。
2. 提出了一种基于服务添加算法的指定密钥选择方法，可以在不影响服务检索效率和稳定性的前提下减少服务添加时间。
3. 分析了所提出的服务添加方法的时间复杂度。此外，建议的服务添加过程被数学建模以分析其效率。
4. 实现了多级索引模型的仿真平台，集成了指定键的选择方法和相应的业务添加操作。实验验证了我们提出的服务添加算法的效率。

## 2. Related word

我们提出了一种经过实验验证的令人信服的指定密钥选择方法，该方法可以在不影响服务检索效率和稳定性的情况下显着提高服务添加效率.

## 3. MULTILEVEL INDEX MODEL FOR EDGE COMPUTING

边缘计算具有分布式处理架构的特征，其中托管可能比例的数据处理以释放网络和后端数据中心的压力。

在边缘计算模型中，由于带宽需求和网络延迟的减少，在边缘服务器中缓存和检索数据可以更加高效。

在边缘计算环境中检索数据如下图所示：



![CPE-6626-FIG-0001-c](https://onlinelibrary.wiley.com/cms/asset/c448fd6e-81d9-4fdd-9b81-9cd3bd25bfcb/cpe6626-fig-0001-m.png)



边缘服务器可以使用多级索引模型，如下图多层次指数模型的框架所示，方便边缘服务的运行和管理。



![CPE-6626-FIG-0002-b](https://onlinelibrary.wiley.com/cms/asset/8d3089bd-66b5-45ec-9d2a-0f5a62b6bc6b/cpe6626-fig-0002-m.png)



#### 3.1 服务的基本定义

*定义 1.*服务表示为一个元组*s =* {• *s, s* • *, O* }，其中 • *s*是输入参数的集合，*s* • 是输出参数的集合，*O*是服务属性的集合，例如，服务质量。

*定义 2.*服务检索表示为一个元组*Re* ( *A, S* ) *=* { *s|* • *s* ⊆  *A ^ s ∈ S* }，其中*A*代表给定参数集，*S*代表服务集。服务检索可以定义为从服务集*S中查找所有输入参数包含在**A中的服务的过程，即**A*下可以调用的所有服务。

#### 3.2 多级指标模型

多级索引模型是基于等价关系建立的，其动机是减少服务检索过程中的冗余。



![CPE-6626-FIG-0003-b](https://onlinelibrary.wiley.com/cms/asset/7cf6ad18-043a-4192-916b-7ae45c13ba97/cpe6626-fig-0003-m.png)



#### 3.3 不同的密钥选择方法

服务库中的服务信息添加操作使用添加算法，以所选服务的输入参数之一为关键字，将服务信息插入到多级索引模型中。

文献中的实验分析假设关键选择方法不会影响服务检索性能，但会对服务检索稳定性产生相当大的影响。如果两个检索请求的响应时间相差很大，则说明检索过程不够稳定。在最先进的方法中，随机密钥选择方法被认为是实现稳定性的最佳密钥选择方法。

## 4. OPTIMIZATION OF SERVICE ADDITION

本节在不影响服务检索效率和稳定性的情况下，提出了一种服务添加算法的指定键选择方法，并将其集成到多级索引模型中，以减少服务添加时间。

分析了所提出的服务添加算法的时间复杂度，进一步建立了服务添加过程的数学模型，分析了服务添加的效率。

#### 4.1 指定键选择方法

主索引模型的服务添加算法:



算法一: 主索引的服务添加

​        输入：一个服务，一个主索引；

​        输出：随服务添加的主索引；

1. 使用密钥选择方法为服务选择密钥；
2. 根据key将服务加入主索引。

部分/完整索引模型的服务添加算法:



算法二.部分/全索引的服务添加

​       输入：一个服务，一个部分/完整的索引；

​       输出：随服务添加的部分/完整索引；

1. 对于服务的每个输入参数
2. ​    {如果输入参数是一个键
3. ​      {判断key映射的key类中是否存在输入相似类，使得其输入集等于服务输入集；
4. ​       如果存在
5. ​         {将服务添加到输入相似类中；
6. ​           返回;}}}
7. 使用密钥选择方法为服务选择密钥；
8. 将服务添加到新的输入相似类中。



算法三.指定密钥选择方法

输入：服务；

输出：服务的密钥；

1. *总和*=0；
2. 对于服务的每个输入参数*a*
3. ​    { *sum* = *sum* + *a.id* ;}
4. *i* = *sum* mod *c* ; // ( *c*表示服务的输入参数的计数。)
5. 返回第*i*个输入参数作为服务的键。



算法四.部分/完整索引的服务添加

输入：一个服务，一个部分/完整的索引；

输出：随服务添加的部分/完整索引；

1. 使用[算法 3](https://onlinelibrary.wiley.com/doi/full/10.1002/cpe.6626?saml_referrer=#cpe6626-fea-0003)选择服务的密钥；
2. 在key映射的key类中判断已有的输入相似类的输入集是否与服务输入集相等；
3. 如果存在
4.    {将服务添加到输入相似类中；
5. ​    返回;}
6. 别的
7. ​    将服务添加到新的输入相似类中；



所提出的指定密钥选择方法可以提高部分和全索引模型的服务添加过程的性能。但是，指定键选择方法不能改进主索引模型的服务添加操作，因为该索引不包含任何输入相似类，其中随机键选择方法性能更好。

#### 4.2 三个多层次指标的服务增加预期

本文以比较服务参数的期望值作为指标来比较附加性能。

指定键的选择方法不影响主索引的加法操作，但可以显着减少部分索引和全索引的服务附加时间。

## 5. EXPERIMENTS AND ANALYSIS

硬件环境：3.00 GHz 的 Inter Core i7-3540M CPU 和 8.00 GB 的 RAM

实验平台：Microsoft Visual Studio 2017 中使用 Visual C# 面向对象开发技术进行开发

每个合成数据集包含 20,000 个服务和 1000 个参数集，每个服务有 10 个输入和 10 个输出参数，即*n* = 10 和*m* = 10。每个检索请求包含 32 个参数。

本实验一共生成了 10 个数据集，每个数据集包含 100 个检索请求，但用于测试稳定性的数据集包含一个检索请求。

我们提出的指定密钥选择方法不仅保持了服务检索过程的稳定性，而且比原始密钥选择和随机密钥选择更好地减少了服务添加时间。为了证明这一点，分别使用原始密钥选择方法、随机密钥选择方法和指定密钥选择方法为业务添加操作生成了三种不同类型的多级索引模型。

从实验结果可以得出结论，本文提出的指定键选择方法在不损失服务检索效率和稳定性的情况下，在部分和全部指标上都显着提高了服务添加效率。

## 6. Conclusion

<mark>本文提出了一种新的服务添加算法，并开发了指定密钥选择方法，以提高边缘计算环境中多级索引模型的服务添加效率。</mark>>尽管所提出的基于服务添加算法的指定密钥选择方法的效率与原始密钥选择方法和主索引模型中的随机密钥选择方法的效率相似，但我们的方法显着减少了服务添加时间约 84部分和全索引模型分别比原始键选择方法高 76% 和 76%，部分和全索引模型分别比随机选择方法高 78% 和 66%。实验结果也符合我们的理论验证。此外，与随机密钥选择方法相比，提出的基于服务添加算法的密钥选择方法不影响服务检索效率和稳定性。作为未来的工作，我们计划将提出的多级索引模型方法集成到现实世界的边缘设备中，进一步优化服务管理能力，提高边缘服务器中服务发现的效率。
