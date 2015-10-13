# lei-search

[![NPM version](https://badge.fury.io/js/lei-search.png)](http://badge.fury.io/js/lei-search)
[![Dependencies Status](https://david-dm.org/leizongmin/lei-search.png)](https://david-dm.org/leizongmin/cn-search)
[![Build Status](https://travis-ci.org/leizongmin/lei-search.png?branch=master)](https://travis-ci.org/leizongmin/lei-search)
[![Coverage Status](https://coveralls.io/repos/leizongmin/lei-search/badge.png?branch=master&service=github)](https://coveralls.io/github/leizongmin/lei-search?branch=master)

[![NPM Stats](https://nodei.co/npm/lei-search.png?downloads=true&stars=true)](https://npmjs.org/package/lei-search)
[![NPM Downloads](https://nodei.co/npm-dl/lei-search.png?months=9)](https://npmjs.org/package/lei-search)

轻量级的中文搜索引擎，基于Redis

本项目原始代码来自 https://github.com/tj/reds 和 https://github.com/sxyizhiren/cn-search

## 安装

```bash
$ npm install lei-search
```

## 使用方法

```js
var searcher=require('lei-search');
var search = searcher.createSearch('pets');
var strs = [];
strs.push('Tobi wants four dollars');
strs.push('Mustachio is a cat');
strs.push('这是一个支持中文的搜索引擎，hello man');

strs.forEach(function(str, i){ search.index(str, i); });


// search who have all words in it.
search
  .query('支持 hello')
  .end(function(err, ids){
    if (err) throw err;
    console.log('Search results for "%s":', query);
    ids.forEach(function(id){
      console.log('  - %s', strs[id]);
    });
});

// search who have either word in it.
search
	.query('中文 Mustachio')
	.type('or')
	.end(function(err, ids){
		if (err) throw err;
		console.log('Search results for "%s":', query);
		ids.forEach(function(id){
		  console.log('  - %s', strs[id]);
		});
	});

```

## License

```
The MIT License (MIT)

Copyright (c) 2015 Zongmin Lei <leizongmin@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

