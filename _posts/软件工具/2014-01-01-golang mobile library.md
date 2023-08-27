---
layout: post
title: golang mobile library
category: 软件工具
tags: software
keywords: 
description: 
---

## Installation[More](https://pkg.go.dev/golang.org/x/mobile/cmd/gomobile)[More2](https://www.imooc.com/article/317158)

```
go install golang.org/x/mobile/cmd/gomobile@latest
gomobile init
ln -s ~/go/bin/gomobile /opt/homebrew/bin/gomobile
ln -s ~/go/bin/gobind /opt/homebrew/bin/gobind

gomobile bind -target=ios hello
```

复制代码 调用

```
import hello.Hello;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        // 省略无关代码
        fab.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // 在这里调用 hello 方法
                Snackbar.make(view, Hello.hello("ray"), Snackbar.LENGTH_LONG)
                        .setAction("Action", null).show();

            }
        });
    }
}
```

## Reference


* [golang/mobile](https://github.com/golang/mobile/)
