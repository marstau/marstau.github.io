---
layout: post
title: indenting spaces must be used in groups of 2
category: errors
tags: error-unresolved
keywords: web
description: 
---	


## ERROR

```
_gh_pages/docs/4.1/about/brand/index.html: line 106, col 1, indenting spaces must be used in groups of 2
_gh_pages/docs/4.1/about/license/index.html: line 106, col 1, indenting spaces must be used in groups of 2
_gh_pages/docs/4.1/about/overview/index.html: line 106, col 1, indenting spaces must be used in groups of 2
_gh_pages/docs/4.1/about/translations/index.html: line 106, col 1, indenting spaces must be used in groups of 2
_gh_pages/docs/4.1/browser-bugs/index.html: line 106, col 1, indenting spaces must be used in groups of 2
```

## Solution

```

....

    </li>
   
  </ul>
```

`/li`和`/ul`之间多了一行空格`   `,去掉即可

```
    </li>
  </ul>
```

## Reference
