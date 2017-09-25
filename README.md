# MkDocs 支持中文搜索

MkDocs 非常好用，但是不支持中文搜索，本项目就是为了解决中文搜索的问题。

>  参考资料：[macOS 使用 mkdocs 生成文档及解决中文搜索问题](http://beautycss.net/2017/01/23/use-mkdocs-on-mac/)

**问题描述：**

1. mkdocs 生成 json 文件时将汉字转成了ascii 码字符；
2. mkdocs 使用的搜索插件 lunr.js本身不支持中文；

>  本项目直接修改源码，直接解决了这两个问题。

**解决方案：**

1. search.py 中的 generate_search_index 方法中的返回值改为：

```
return json.dumps(page_dicts, sort_keys=True, ensure_ascii=False, indent=4)
```

2. 使用修改后的 [lunr.js](https://github.com/codepiano/lunr.js/blob/master/lunr.js) 替换 lunr.min.js


## 安装

如果你已经安装了 mkdocs ，请先卸载掉：
```
$ pip uninstall mkdocs
```

然后 clone  本项目到本地，切换到项目根目录，再进行安装：
```
$ python setup.py install
```

## 使用

用法跟源来的 MkDocs 一样

 [MkDocs wiki](https://github.com/mkdocs/mkdocs/wiki) 
