---
layout: post
title: Navicat for MySQL
category: 软件工具
tags: software
keywords: 
description: 
---

## 导入.sql文件规范(MySQL 5.0)

### 存储过程

#### 文件末尾要以回车结束


```
1 - 	…
2 - 	DELIMITER ;
```

则须如下(最后一行为回车)

```
1 - 	…
2 - 	DELIMITER ;
3 -		
```

否则无法正确导入

#### ELSE END IF;

```
1 -		ELSE
2 -		END IF;
```

去掉ELSE

```
1 - 	END IF;
```


## Reference
