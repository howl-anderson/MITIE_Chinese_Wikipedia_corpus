# 中文维基百科 MITIE 语料库

这个项目旨在为训练 [MITIE](https://github.com/mit-nlp/MITIE) 中文语料库提供工具和指南. 通常情况下，训练这个模型，需要一台高配置、高网速的服务器大约运行三天，才能训练完毕，为了节约时间，本项目也将提供预训练好的模型。

## 从零开始训练
### 构建维基百科语料库

见项目 [chinese-wikipedia-corpus-creator](https://github.com/howl-anderson/chinese-wikipedia-corpus-creator)，维基百科的语料库的最终数据目录为 `third-party/chinese-wikipedia-corpus-creator/token_cleaned_plain_files`。可以使用两种方式获得数据：直接下载已经预处理好的语料库 或者 从零开始处理语料库

#### 直接下载已经预处理好的语料库
直接下载 `chinese-wikipedia-corpus-creator` 已经处理好的文件，下载地址在 [Release of chinese-wikipedia-corpus-creator](https://github.com/howl-anderson/chinese-wikipedia-corpus-creator/releases)，下载后放置到 `third-party/chinese-wikipedia-corpus-creator/token_cleaned_plain_files`

#### 从零开始处理语料库
将 `chinese-wikipedia-corpus-creator` 源代码下载或者克隆至 `third-party/chinese-wikipedia-corpus-creator`，按照该项目文档的说明，运行相关代码，产生中文维基百科语料库。确保最后的输出文件位于 `third-party/chinese-wikipedia-corpus-creator/token_cleaned_plain_files`

### 构建 `MITIE` 工具

#### 获取 `MITIE` 源代码
这里选择将 `MITIE` clone 至本项目的 `third-party` 目录：

```console
$ git clone https://github.com/mit-nlp/MITIE.git
```

#### 编译 `MITEIE`

MITIE 是一个工具的集合包，本项目所需的只是其中的 `wordrep` 工具

```console
$ cd third-party/MITIE/tools/wordrep
$ mkdir build
$ cd build
$ cmake ..
$ cmake --build . --config Release
```

### 训练模型

```console
$ ./third-party/MITIE/tools/wordrep/build/wordrep --count-words 800000 --word-vects --basic-morph --cca-morph ./third-party/chinese-wikipedia-corpus-creator/token_cleaned_plain_files
```

## 下载预训练好的模型

可下载的模型列表见 [releases](https://github.com/howl-anderson/MITIE_Chinese_Wikipedia_corpus/releases) (已提供针对中国用户的快速下载链接)

## 如何贡献代码

请阅读 [CONTRIBUTING.md](https://github.com/howl-anderson/MITIE_Chinese_Wikipedia_corpus/CONTRIBUTING.md) 并向我们发送 pull requests.

## 版本控制方案

使用 [SemVer](http://semver.org/) 的标准方案. 访问 [tags on this repository](https://github.com/your/project/tags) 可了解所有版本信息.

## 作者

* **Xiaoquan Kong** - *Initial work* - [howl-anderson](https://github.com/howl-anderson)

全体贡献者信息在 [contributors](https://github.com/your/project/contributors) 处可见。

## 授权协议

本项目采用 MIT License - 详情请见 [LICENSE.md](LICENSE.md)

## 致谢
* `MITIE` 软件编译的部分，参考了 [WANG Guan](https://github.com/crownpku) 的博文 [用Rasa NLU构建自己的中文NLU系统](http://www.crownpku.com/2017/07/27/%E7%94%A8Rasa_NLU%E6%9E%84%E5%BB%BA%E8%87%AA%E5%B7%B1%E7%9A%84%E4%B8%AD%E6%96%87NLU%E7%B3%BB%E7%BB%9F.html)

