---
title: Hexo 插件、注意事项 和主题相关问题
date: 2016-11-30 10:03:46
authors:
- EvanWang
categories:
- Workflow
- Hexo
tags:
- Hexo
- Hexo Plugin
- Hexo Tips
- Hexo Matters
---

# Hexo插件

## 图片插件

- [Hexo七牛同步插件](https://github.com/gyk001/hexo-qiniu-sync)

<!-- more -->

# Hexo Tips

- Hexo 是有[中文文档](https://hexo.io/zh-cn/docs/)的，当然更推荐看[英文文档](https://hexo.io/docs/)

- 关于几个文件夹功能的释义
  - `scaffolds` 为模板文件夹，模板用于预先定义 `new` 出来的文章的 `layout`
  - `source` 内 `_drafts` 文件夹用于放置草稿，使用 `hexo --draft` 可查看所有草稿文章；草稿完稿后可以使用 `publish` 命令发布到 `_post` 文件夹内，等待 `generate`

- 自定义的其他模板和 `post` 模板相同，`new` 出来的文章都将储存到 `source/_posts` 文件夹

- 当你不想你的文章被发布，同时又不想删除文章，将文章的 `Front-Matter` 中的 `layout`: 设为 `false`

- 文章的 `Front-matter` 采用 `YAML` 语法格式，多个标签与分类不是用逗号隔开，而是采用 `YAML` 中的 列表/并列 写法

- `Hexo` 支持更强大的 `quote` 块：可以添加引用作者、来源、链接等；在有这些需求的时候可以引用

    ```swig
    {% blockquote [author[, source]] [link] [source_link_title] %}
    content
    {% endblockquote %}
    ```

- `Hexo` 支持更强大的 `code` 块：支持为 `code` 块添加标题和链接；当我们需要引用某个链接内的代码时可以使用，一般情况下使用 `md` 的代码块语法即可

    ```swig
    {% codeblock [title] [lang:language] [url] [link text] %}
    code snippet
    {% endcodeblock %}
    ```

- 引入 `gist` 时，插入 `fileName` 似乎会失败，所以，引入 `gist` 时只需要使用 `gist hash-id` 即可

    ```swig
    {% gist 5b3ee7efd535ab63cd56 %}
    ```
- Hexo 支持更使用特定的语法，插入指定大小的图片，如下：

    ```html
    // 语法
    {% img [class names] /path/to/image [width] [height] [title text [alt text]] %}
    
    // 实例
    {% img full-image /hexo-experiences/PL01.jpg 180 180 hello %}

    // 生成的代码
    <img src="/blog/hexo-experiences/PL01.jpg" class="full-image" width="180" height="180" title="hello">
    ```

    值的注意的几点：

    - 路径名必须以 `/` 开始，否则会解析出错
    - 路径是相对于 `conifg` 内的 `root` 的，这一点挺坑，可以在 `source/` 下新建一个 `uploads` 文件夹用于专门放置这些图片资源

            {\% img hi /uploads/images/test.jpg 100 100 hello hello %}
    - 图片宽高只能使用数值，不能包含字符串，也不能是百分数
    - 最后一个字段可以为图片添加标题

- 引入某个文件中的代码，使用 `include_code`

    ```swig
    // 语法
    {% include_code [title] [lang:language] path/to/file %}
    // 实例
    {% include_code DOMUtil lang:javascript demo.js %}
    ```

    值得注意的是：`code` 代码所在的文件必须在 `downloads/code/` 目录下，否则无法获取
    

- 引用其他文章的路径，基本功能不大

    ```swig
    // 语法
    {% post_path slug %}

    // 实例
    {% post_path OS-Brief-Intro %} // >> /blog/2016/05/03/OS-Brief-Intro/
    ```

- 引用其他文章的链接，用处很大，但是有一个小坑

    ```swig
    // 语法
    {% post_link slug [title] %}
    
    // 实例
    {% post_link OS-Brief-Intro 操作系统 %}
    ```
    
    小坑：不能放在一段的段首，否则 `md` 文档或解析错误，出现莫名奇妙的 bug
 
- 引用文章的资源：获取到的是文章对应 `asset` 目录下的资源

    ```swig
    // 语法
    {% asset_path slug %}
    {% asset_img slug [title] %}
    {% asset_link slug [title] %}

    // 实例
    {% asset_path 01.png %}
    {% asset_img 01.png 图片 %}
    {% asset_link 01.png 图片 %}
    ```

- 将 `_config.yml` 文件中的 `post_asset_folder` 选项设为 `true`，便可在 `new` 一篇新文章的同时创建对应的资源文件夹。引用资源文件夹内的文件请使用上面 `引用文章的资源` 中使用的方法，可以防止首页展示时链接错误的问题。

- [链接：数据文件](https://hexo.io/zh-cn/docs/data-files.html)

- `hexo generate --watch` 可以监听文件变动，自动 `generate`

- `hexo g -f` 可以强制重新生成，防止一些更改后无法 `generate` 的清理

- 自动提交脚本：`deploy.sh`

    ```shell
    hexo generate -f
    echo ">>>>>>What is your commit message to blog-material repo?"
    read COMMIT1
    git add --all
    git commit -m "$COMMIT1"
    echo "commited"
    git push
    echo "pushed all to blog-material repo"
    cd public
    echo ">>>>>>What is your commit message to blog repo?"
    read COMMIT2
    git add --all
    git commit -m "$COMMIT2"
    echo "commited"
    git push
    echo "pushed all to blog repo"
    cd ../
    ```

- 实现 RSS 订阅：[hexojs/hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed)

- Hexo 的 `markdown` 解析引擎不支持脚注，可以使用插件实现。

    > 但是笔者在使用了 [LouisBarranqueiro/hexo-footnotes](https://github.com/LouisBarranqueiro/hexo-footnotes) 之后发现 hexo server 命令无法使用了。

    更换默认的 `md` 渲染引擎 `hexo-renderer-marked`，改为 `hexo-renderer-markdown-it`，见 [配置文档](http://yangfch3.com/2016/05/08/hexo-experiences/hexo-renderer-marked-it.txt)。几大优点：
    - 支持脚注解析
    - 支持上下标
    - 支持 emoji – 需要额外配置


# Hexo主题

## NexT

- `NexT` 的一些菜单页（如：标签页、分类页、归档页）需要自己添加，方法见 [官网文档](http://theme-next.iissnan.com/theme-settings.html)

- `NexT` 的 `i18n` 可以在 theme/next/language 下的 .yml 文件下自己定制

- `NexT` 支持文本居中的引用

    ```swig
    {% centerquote %}blah blah blah{% endcenterquote %}

    {% cq %} blah blah blah {% endcq %}
    ```

- NexT 中的图片可以自由地突破容器宽度的限制（扩大 26%）

    ```swig
    {% fullimage /image-url, alt, title %}

    {% fi /image-url, alt, title %}
    ```

- 在为文章创建 Tags 的时候，避免标签内出现 “&”，否则生成的 .xml 文件在浏览器端会解析错误，并且订阅功能也会出现故障

## 主题编写

- Hexo 提供的辅助函数中截取一段长文字的前 n 个字符

    ```swig
    // swig 的写法
    {% truncate('long string', {length: n}) %}

    // 实例
    {% truncate(post.description, {length:n}) %}
    ```
- 在 swig 中，胡子或胡子百分号内不能再使用胡子或胡子百分号

- DIY 主题，写法参考 [官网教程](https://github.com/yangfch3/Dandelion)


# 参考文章

- [使用 Hexo 与 NexT 搭建博客的避坑总结](http://yangfch3.com/2016/05/08/hexo-experiences/)